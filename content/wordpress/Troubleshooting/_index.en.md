---
title: "Troubleshooting the oopspam WordPress Plugin"
linkTitle: "Troubleshooting"
date: 2024-10-21T11:02:05+06:00
weight: 7
draft: false
# search related keywords
keywords: ["troubleshooting", "false positive", "flagged as spam", "still getting spam", "api limit", "warning", "notifications"]
faq: true
description: "Fixes for common oopspam plugin problems: real messages flagged as spam, spam still getting through, API limit warnings and missing notifications."
---

Start with the problem that matches what you see. If none of them fits, [contact support](https://www.oopspam.com/#contact) and include your site URL and, if you can, an example entry from the plugin's [logs](../form-entries/).

## Why are legitimate form submissions being flagged as spam?

Check these settings in _oopspam Anti-Spam → Settings_, in this order:

1. **Consider short messages as spam.** If your form's message (textarea) field is optional, or people often write fewer than 20 characters, turn this setting off. Otherwise short but genuine messages are blocked.
2. **Sensitivity Level.** Keep it at the recommended level 3 (Moderate). If you still see false positives at level 3, turn on the experimental **Reduce False Positives** option below the slider.
3. **Country and language filters.** A country allowlist or blocklist, or a language allowlist, blocks every submission that doesn't match, however genuine it is. Check that your real customers' countries and languages are allowed.
4. **IP filtering.** **Block VPNs** and **Block Cloud Providers** also block real people who use a VPN or a corporate proxy. Turn them off to test.
5. **Minimum time between page load and submission.** Browser autofill can complete a form in a second or two. If you set this above 2–3 seconds, lower it.
6. **Manual Moderation.** A blocked keyword matches anywhere in a message, regardless of capitalization, so a short or common word can block real messages.

Then report the entry: open **Form Spam Entries**, hover over it and click **Not Spam**. oopspam learns from your reports, so the same kind of message is far less likely to be blocked again. See [Reporting](../../report/) for details.

Further reading: [Why legitimate form submissions get flagged as spam, and how to reduce false positives](https://www.oopspam.com/blog/why-legitimate-form-submissions-get-flagged-as-spam-and-how-to-reduce-false-positives).

## Why am I still getting spam with oopspam installed?

1. **Is the form protected?** Make sure **Activate Spam Protection** is checked for the form plugin you use. Each form plugin has its own toggle, and only comments are protected by default. If the submission isn't in **Form Spam Entries** or **Form Valid Entries**, oopspam never saw it.
2. **Is the right field being checked?** The plugin analyzes the first textarea field. If your form has several, enter the ID of the message field in **The main content field ID** for that form plugin.
3. **Report what got through.** In **Form Valid Entries**, hover over the entry and click **Spam**. Reports teach oopspam what spam looks like on your site.
4. **Tighten the filters for the pattern you see.** Spam from countries you don't serve → a country blocklist or allowlist. Messages in a language you don't support → the language allowlist. Floods from the same sender → rate limiting. Bots on servers → **Block Cloud Providers**. One persistent sender or phrase → **Manual Moderation**.
5. **Raise detection.** Move the **Sensitivity Level** slider up a step, or turn on the experimental **Extra Screening** option.
6. **Is the spam relevant to your business but still unwanted?** Sales pitches and off-topic requests aren't always classic spam. [Contextual Detection](../configuration/#contextual-detection) judges each message against a description of your business.

Further reading: [So, you're using oopspam and still getting spam?](https://www.oopspam.com/blog/so-youre-using-oopspam-and-still-getting-spam)

## Why do I see an API limit warning when I'm on a paid plan?

1. Confirm that you have a valid API key. Make sure you have registered on the [oopspam Dashboard](https://app.oopspam.com) and copied the key.
2. Paste the API key into _My API Key_ in the oopspam WordPress settings.
3. Select _oopspam Dashboard_ from _I got my API Key from_.
4. Check _Activate Spam Protection_ for the contact form plugin you have.
5. Wait for the first form or comment submission to come in.
6. The API usage numbers update with each submission, and the warning disappears.

If the warning stays, check that a payment didn't fail. After three failed payment attempts the API key is restricted until billing details are updated. See [Account](../../account/#how-to-update-my-billing-information).

## How can I check that spam protection is working?

Submit your form, or post a comment, using one of the test email addresses or the sample message on the [Testing](../testing/) page. You should see your form's error message, and the entry should appear in **Form Spam Entries**. If it goes through, see "Why am I still getting spam" above.

## Why are my form notification emails not arriving?

First check **Form Spam Entries**. Blocked submissions don't trigger your form's notification email, so a genuine message that was flagged looks like a missing email. If it's there, mark it **Not Spam** and see the false positives section above.

If the submission is in **Form Valid Entries**, oopspam allowed it and the problem is email delivery. These guides cover the usual causes for each form plugin:

- [WPForms not sending email notifications](https://www.oopspam.com/blog/wpforms-notification-issue)
- [Gravity Forms not sending email notifications](https://www.oopspam.com/blog/gravity-forms-notification-issue)
- [Elementor Forms not sending email notifications](https://www.oopspam.com/blog/elementorforms-notification-issue)
- [Fluent Forms not sending email notifications](https://www.oopspam.com/blog/fluent-forms-notification-issue)
- [WS Form not sending email notifications](https://www.oopspam.com/blog/wsform-notification-issue)

## Why do all submissions show the same IP address or the wrong country?

Your site is probably behind a CDN or proxy such as Cloudflare or Sucuri, so the plugin sees the proxy's IP address instead of the visitor's. Turn on **Trust proxy headers** under [Miscellaneous Settings](../configuration/#miscellaneous-settings). Only enable it if you trust your proxy service. Country filters, rate limiting and IP blocking all depend on the real visitor IP.

## Why can't I find the Trusted Countries setting?

**Trusted Countries** is only available when the privacy setting **Do not analyze IP addresses** is off. Without the visitor's IP address, the plugin can't tell which country a submission came from.

## Why is Contextual Detection blocking or allowing the wrong messages?

Contextual Detection judges the message text against your **Website Context** description, so it needs a message to work with. Use it only on forms with a required textarea field. Then make the context more specific: list the kinds of messages you expect and the kinds you consider spam, as in the [example on the Configuration page](../configuration/#contextual-detection). While Contextual Detection is on, standard spam detection is turned off.

## How do I let a blocked visitor contact me another way?

Form plugins have their own spam message setting in the oopspam settings, for example **Elementor Form Spam Message**, and WooCommerce has **WooCommerce Spam Order & Registration Message**. Use it to tell blocked visitors how else to reach you, such as an email address. The message is only shown to submissions oopspam blocks, so your address stays hidden from everyone else.

## Why did my spam and valid entries disappear?

The **Form Spam Entries** and **Form Valid Entries** tables are emptied automatically once a month by default. You can change this to every two weeks under [Additional settings](../configuration/#additional-settings), and use **Export to CSV** on either table to keep a copy. Entries you reported stay visible on the [Reported page](https://app.oopspam.com/ReportedSpam) in the oopspam Dashboard until they are resolved.

## Where do spam comments go?

By default oopspam moves spam comments to the Spam folder under _Comments_. To send them to the Trash instead, change **Move spam comments to** under [Additional settings](../configuration/#additional-settings).

## Why is my WordPress site search getting spam queries?

Spam bots also abuse the WordPress search box, flooding it with spam queries. Turn on **Protect against internal search spam** under [Additional settings](../configuration/#additional-settings).

Further reading: [How to protect your WordPress website from internal search spam](https://www.oopspam.com/blog/how-to-protect-your-wordpress-website-from-internal-search-spam)

## How do I stop fake orders and card testing in WooCommerce?

oopspam protects WooCommerce registration, login and checkout, and adds fraud checks: honeypot fields, blocking of orders from unknown origins, failed-payment limits per IP, and blocking by order amount or billing address. See the [WooCommerce settings](../woocommerce/) for each option.

Further reading: [How to protect your store from fake orders, card testing and checkout spam](https://www.oopspam.com/blog/how-to-protect-your-store-from-fake-orders-card-testing-and-checkout-spam)

## Still stuck? Contact support

[Contact support](https://www.oopspam.com/#contact) with your site URL and, if you can, an example entry. Looking for the plugin itself? See [oopspam for WordPress](https://www.oopspam.com/wordpress).
