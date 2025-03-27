---
title: "Multisite / Network"
breadcrumbs: false
date: 2025-03-27T11:02:05+06:00
weight: 4
draft: false
keywords: ["multisite", "network", "wordpress", "forms", "spam protection"]
description: "Quickly configure the OOPSpam WordPress plugin for multisite environments. This guide covers API key setup, form integration, and enabling spam protection for various plugins and features."
---

# OOPSpam WordPress Multisite Configuration

The OOPSpam WordPress plugin fully supports multisite environments. This guide explains how to configure the plugin globally using your `wp-config.php` file.

## Basic Configuration

Add your API key to enable spam protection:

```php
define( 'OOPSPAM_API_KEY', 'YOUR_KEY' );
```

## Form Integration Settings

Enable spam filtering for specific form types by adding these definitions to your `wp-config.php`. Set to `true` to enable or `false` to disable.

### Popular Form Plugins
- **Contact Form 7**: `define( 'OOPSPAM_IS_CF7_ACTIVATED', true );`
- **WPForms**: `define( 'OOPSPAM_IS_WPF_ACTIVATED', true );`
- **Gravity Forms**: `define( 'OOPSPAM_IS_GF_ACTIVATED', true );`
- **Ninja Forms**: `define( 'OOPSPAM_IS_NJ_ACTIVATED', true );`

### Page Builder Forms
- **Elementor Pro**: `define( 'OOPSPAM_IS_EL_ACTIVATED', true );`
- **Beaver Builder**: `define( 'OOPSPAM_IS_BB_ACTIVATED', true );`
- **Bricks Builder**: `define( 'OOPSPAM_IS_BR_ACTIVATED', true );`
- **Kadence Blocks**: `define( 'OOPSPAM_IS_KB_ACTIVATED', true );`

### Membership & eCommerce
- **WooCommerce**: `define( 'OOPSPAM_IS_WOO_ACTIVATED', true );`
- **MemberPress**: `define( 'OOPSPAM_IS_MPRESS_ACTIVATED', true );`
- **Paid Memberships Pro**: `define( 'OOPSPAM_IS_PMP_ACTIVATED', true );`
- **Ultimate Member**: `define( 'OOPSPAM_IS_UMEMBER_ACTIVATED', true );`

### Newsletter & Marketing
- **MailChimp for WP**: `define( 'OOPSPAM_IS_MC4WP_ACTIVATED', true );`
- **MailPoet**: `define( 'OOPSPAM_IS_MPOET_ACTIVATED', true );`

### Other Supported Forms
- **Jetpack Forms**: `define( 'OOPSPAM_IS_JFORM_ACTIVATED', true );`
- **SureForms**: `define( 'OOPSPAM_IS_SURE_ACTIVATED', true );`
- **WordPress Registration**: `define( 'OOPSPAM_IS_WPREGISTER_ACTIVATED', true );`
- **GiveWP Donation**: `define( 'OOPSPAM_IS_GIVE_ACTIVATED', true );`
- **Fluent Forms**: `define( 'OOPSPAM_IS_FF_ACTIVATED', true );`
- **WS Form**: `define( 'OOPSPAM_IS_WS_ACTIVATED', true );`
- **Formidable**: `define( 'OOPSPAM_IS_FABLE_ACTIVATED', true );`
- **Toolset Forms**: `define( 'OOPSPAM_IS_TS_ACTIVATED', true );`
- **Piotnet Forms**: `define( 'OOPSPAM_IS_PIONET_ACTIVATED', true );`
- **wpDiscuz Comments**: `define( 'OOPSPAM_IS_WPDIS_ACTIVATED', true );`
- **Forminator**: `define( 'OOPSPAM_IS_FORMINATOR_ACTIVATED', true );`

## Example Configuration

Here's a complete example of how to configure multiple forms in your `wp-config.php`:

```php
// OOPSpam Configuration
define( 'OOPSPAM_API_KEY', 'your-api-key-here' );
define( 'OOPSPAM_IS_CF7_ACTIVATED', true );
define( 'OOPSPAM_IS_WOO_ACTIVATED', true );
define( 'OOPSPAM_IS_WPREGISTER_ACTIVATED', true );