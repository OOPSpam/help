---
title: "Hooks"
date: 2023-06-01T11:02:05+06:00
lastmod: 2023-06-01T11:02:05+06:00
weight: 4
draft: false
# search related keywords
keywords: ["hook" , "filter", "action"]
---

You can overwrite spam filtering in the OOPSpam WordPress plugin using the `oopspam_check_for_spam` filter.

In your theme's `functions.php` page or anywhere else, add the following code:

```php
add_filter('oopspam_check_for_spam', 'mycustom_spam_check', 10, 3);

function mycustom_spam_check($message, $ip, $email) {
    // Your custom logic

    // Return 0 for ham/not spam or 6 for spam.
    return 6;
}
```

The returned value can be any value from 0 to 6. We recommend keeping it simple and returning `0` for not spam, and `6` for spam entries.
