---
title: "WP-CLI"
date: 2026-08-27T11:02:05+06:00
weight: 8
draft: false
# search related keywords
keywords: ["wp-cli", "command line", "settings", "automation", "import", "export"]
description: "Manage the OOPSpam WordPress plugin from the command line with WP-CLI. View status, get and set settings, and import or export your configuration."
---

The OOPSpam WordPress plugin ships with a set of WP-CLI commands that let you manage its settings from the command line. This is useful for automating configuration, rolling out the plugin across many sites, or managing settings on servers where you don't have access to the WordPress dashboard.

All commands live under the `oopspam` namespace and require [WP-CLI](https://wp-cli.org/) to be installed:

```bash
wp oopspam <command>
```

The available commands are:

| Command | Purpose |
| --- | --- |
| `wp oopspam status` | Show the plugin status and configuration overview |
| `wp oopspam get` | Read one or all plugin settings |
| `wp oopspam set` | Update a single setting |
| `wp oopspam set-many` | Update multiple settings from JSON |
| `wp oopspam export` | Export settings to a JSON file or stdout |
| `wp oopspam import` | Import settings from a JSON file |
| `wp oopspam reset` | Reset all settings to their defaults |

## Status

Show an overview of the plugin configuration, including the plugin version, whether an API key is configured, and the rate limiting state:

```bash
wp oopspam status
```

Example output:

```text
+----------------+----------------------+
| field          | value                |
+----------------+----------------------+
| plugin_version | 1.2.78               |
| configured     | yes                  |
| api_key        | 1234************5678 |
| api_key_source | dashboard            |
| rate_limiting  | yes                  |
| site_url       | https://example.com   |
| multisite      | no                   |
+----------------+----------------------+
```

The API key is masked for security, so it's safe to include this output in logs or support requests.

## Get settings

Read the current plugin settings. Without arguments, prints the whole settings collection as a table:

```bash
wp oopspam get
```

Pass a setting name to read a single value. Dotted paths are supported, so you can read a nested value inside an option:

```bash
wp oopspam get oopspamantispam_settings.oopspam_api_key
```

Use the `--format` flag to control the output. The available formats are `table` (default), `json`, and `plain`:

```bash
wp oopspam get --format=json
wp oopspam get oopspamantispam_settings.oopspam_api_key --format=plain
```

## Set a setting

Update a single setting. Dotted paths are supported, and JSON values are decoded automatically, so you can set structured data:

```bash
wp oopspam set oopspamantispam_settings.oopspam_api_key "abcdef123456"
wp oopspam set oopspamantispam_ratelimit_settings '{"oopspam_is_rt_enabled":"1","oopspamantispam_ratelimit_ip_limit":50}'
wp oopspam set oopspam_countryblocklist '["CN","RU"]'
```

## Set multiple settings

Update several settings at once from a JSON object. You can pass either a map of option keys to full values, or a map of dotted paths to values:

```bash
wp oopspam set-many '{"oopspamantispam_settings.oopspam_spam_message":"Blocked","oopspamantispam_settings.oopspam_api_key":"abc123"}'
```

On a multisite network, add `--all-sites` to apply the changes to every site:

```bash
wp oopspam set-many '{"oopspam_countryblocklist":["CN"]}' --all-sites
```

## Export settings

Export all plugin settings to a JSON file. The exported file can be restored on the same site, moved to another site, or imported through the plugin's Tools tab in the WordPress dashboard:

```bash
wp oopspam export /tmp/oopspam-settings.json
```

If you omit the file path, the JSON is printed to stdout, so you can redirect it:

```bash
wp oopspam export > oopspam-settings.json
```

## Import settings

Import settings from a JSON file produced by `wp oopspam export` or by the plugin's Tools tab:

```bash
wp oopspam import /tmp/oopspam-settings.json
```

By default, existing settings are preserved and imported values override them (a merge). Pass `--replace` to replace each imported option entirely:

```bash
wp oopspam import /tmp/oopspam-settings.json --replace
```

On a multisite network, add `--all-sites` to import the settings into every site:

```bash
wp oopspam import /tmp/oopspam-settings.json --all-sites
```

{{< callout type="info" >}}
  The export format is shared between WP-CLI and the plugin's Tools tab in the WordPress dashboard. A file exported from one can be imported with the other.
{{< /callout >}}

## Reset settings

Reset every plugin setting back to its default state. A confirmation prompt is shown first, which you can skip with `--yes`:

```bash
wp oopspam reset
wp oopspam reset --yes
```

On a multisite network, add `--all-sites` to reset the settings on every site:

```bash
wp oopspam reset --yes --all-sites
```

## Multisite networks

The commands that change settings accept an `--all-sites` flag: `set-many`, `import`, and `reset`. On a multisite network, this applies the command to every site in the network. On a single site, the flag is ignored and the command runs for the current site only, with a warning.
