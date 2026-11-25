---
title: "Bubble.io Spam Protection Plugin"
linkTitle: "Bubble.io"
date: 2024-10-21T11:02:05+06:00
lastmod: 2026-11-25T12:30:00+04:00
weight: 5
draft: false
# search related keywords
keywords: ["bubble"]
description: "Install the oopspam plugin for Bubble.io to check form submissions for spam inside your Bubble app workflows."
---

The [oopspam Bubble plugin](https://bubble.io/plugin/oopspam-spam-detection-1582908608700x936823858020745200) checks contact forms, sign-ups, orders, reviews, comments and any other user input for spam inside your Bubble workflows, without a CAPTCHA.

For a full walkthrough with screenshots, see [Spam protection for Bubble.io](https://www.oopspam.com/blog/spam-protection-for-bubble.io).

!["The finished contact form workflow in Bubble"](https://www.oopspam.com/blog/assets/posts/bubbleio-oopspam/v2/workflow-overview.png)

## Setup

1. Copy your API key from the [oopspam dashboard](https://app.oopspam.com/).
2. In the Bubble editor, go to *Plugins* → *Add plugins*, search for **oopspam** and click *Install*.
3. Open the installed plugin and paste your key into **oopspam API key**.
4. In the *Design* tab, drag the **oopspam Visitor IP** element onto each page that has a form. It's invisible and detects the visitor's IP address and your app's domain.
5. In your form's workflow, add *Plugins* → **Check for spam (oopspam)** and fill in the fields below.
6. Add **Terminate this workflow** with the condition *Result of step X (Check for spam (oopspam))'s Is it spam? is yes*, then add your normal steps, such as *Send email*, after it.

## Check for spam (oopspam)

| Field | What to enter |
|---|---|
| **Content** | The message input's value |
| **Email** | The email input's value (optional) |
| **Sender IP** | *oopspamVisitorIP A's IP* |
| **Your domain** | *oopspamVisitorIP A's Your domain* |
| **Context** | Optional. A description of your website for [contextual detection](https://www.oopspam.com/blog/introducing-contextual-spam-detection). Leave empty for standard detection. |

The action returns:

| Value | Meaning |
|---|---|
| **Is it spam?** | *yes* when the score is at or above your threshold (default 3) |
| **Score** | 0 (clean) to 6 (spam) |
| **Reason** | Why it was flagged, e.g. "spam content, disposable email" |
| **Spam words** | Spam words found in the content |
| **Error** | Filled only if the check couldn't run |

### Options

All options are optional. Leave a field empty to skip that filter.

| Option | What it does |
|---|---|
| **Allowed languages** | Only accept these languages, e.g. `en, it` |
| **Allowed countries** | Only accept submissions from these countries, e.g. `us, it` |
| **Blocked countries** | Block submissions from these countries, e.g. `ru, cn` |
| **Block short content** | On by default. Messages shorter than 20 characters count as spam |
| **Block disposable email** | Block temporary email addresses |
| **Block VPN** | Block VPN, proxy and Tor IPs |
| **Block data center IPs** | Block submissions from cloud providers |
| **Log to oopspam dashboard** | Save each check in your oopspam dashboard |
| **Spam threshold** | The score at which *Is it spam?* becomes yes. Default 3. Higher is less strict |
| **Treat API errors as spam** | Off by default, so submissions go through if the check can't run. Turn on to block them instead |

When **Context** is set, only the content is judged against it, and the score is either 0 or 6. The IP, email, VPN, data center, country and language options are not applied.

## Report spam / not spam (oopspam)

Use this action to report detection mistakes. Pass the same content, email, Sender IP, domain and context as the original check, and set **Should be spam** to *yes* for spam that got through or *no* for a real message that was blocked. A common setup is a *Mark as spam* and *Not spam* button next to each submission on an admin page.

See also [the reporting documentation](/report/).

## Upgrading from the old version

1. Go to *Plugins* → *oopspam* and upgrade the plugin.
2. Paste your key into the new **oopspam API key** field.
3. Add the **oopspam Visitor IP** element to each page with a form.
4. Replace the old *Check for spam* step with **Check for spam (oopspam)**. Bubble's issue checker flags every step that still uses the old call.
5. Change the terminate condition from *Score ≥ 3* to *Is it spam? is yes*.
6. Optionally uninstall the IP Geo plugin. It's no longer needed.

You no longer need to enter `[""]` in empty fields.

## Troubleshooting

| Problem | Fix |
|---|---|
| Error: "Missing API key" | Enter your key in the plugin settings. |
| Error: "401: Invalid API key" | Copy the key again from the dashboard. |
| Error: "429: Rate limit / quota exceeded" | You've used your monthly checks. Upgrade or wait for the reset. |
| Visitor IP is empty | An ad blocker may be blocking detection. Make sure the Visitor IP element is on the form's page. |
| VPN or country options are ignored | **Context** is set. Clear it to use standard detection. |
| Real messages are flagged | Check **Reason** in the debugger, raise the threshold or adjust the filter, and report the message as not spam. |

## Next

Dive right into the following section to get started:

{{< cards cols="4">}}
{{< card link="https://www.oopspam.com/docs/" title="oopspam API ↗" icon="code" subtitle="Integrate custom solutions with the oopspam API." >}}
{{< card link="https://help.oopspam.com/wordpress/" title="WordPress" icon="table" subtitle="Comprehensive guide to the oopspam WordPress plugin." >}}
{{< card link="https://help.oopspam.com/other-integrations/" title="Other integrations" icon="lightning-bolt" subtitle="Incorporate oopspam into Zapier, Make, n8n or Bubble.io workflows." >}}
{{< card link="https://help.oopspam.com/report/" title="Report" icon="microphone" subtitle="Train oopspam to adapt to your specific use case." >}}
{{< /cards >}}
