---
title: "Hooks"
date: 2024-10-21T11:02:05+06:00
weight: 4
draft: false
# search related keywords
keywords: ["hook" , "filter", "action"]
---

The plugins comes with two hooks:

| Hook      | Purpose      |
| ------------- | ------------- |
| `oopspam_check_for_spam` | Overwrite spam filtering. Add your custom logic. |
| `oopspam_woo_disable_honeypot` | Disable honeypot for WooCommerce integration |


## Adding custom spam rule

You can overwrite spam filtering in the OOPSpam WordPress plugin using the `oopspam_check_for_spam` filter and return a score based on your own logic.

In some cases where you can use it:

- Allow and block certain IPs
- Allow and block certain emails
- Block based on some keywords
- and more.

In your theme's `functions.php` file or anywhere else, add the following code:

```php
add_filter('oopspam_check_for_spam', 'mycustom_spam_check', 10, 3);
function mycustom_spam_check($message, $ip, $email) {
    // Your custom logic
    // Return 0 for ham/not spam or 6 for spam.
    return 6;
}
```

The returned value can be any value from `0` to `6`.

> We recommend keeping it simple and returning `0` for not spam, and `6` for spam entries.

## Disable Honeypot in WooCommerce

While honeypot protection helps block bots, it may also block users using password managers or similar browser extensions to autofill forms. To prevent this, you can disable the honeypot and rely on IP and email reputation to assess spam risk.

To disable the honeypot, add the following code to the `functions.php` file or elsewhere in your theme:

```php
add_filter('oopspam_woo_disable_honeypot', '__return_true');
```