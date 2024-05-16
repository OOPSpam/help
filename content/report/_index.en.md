---
title: "Reporting"
date: 2024-05-15T10:42:26+06:00
lastmod: 2024-05-15T10:42:26+06:00
icon: "ti-agenda"
description: "Learn how to report false positives and false negatives"
type : "docs"
---

The OOPSpam API takes an optimistic approach and avoids blocking messages unless it's confident they are spam. However, false positives (legitimate messages marked as spam) and false negatives (spam messages marked as legitimate) can still occur.
There are various reasons for false positives and false negatives, such as:

IP addresses previously used for spamming but now in different hands, retaining a bad reputation.
Messages incorrectly flagged as blocked or not blocked.

To minimize these occurrences, it's essential to train the OOPSpam API's standard model with the specific spam and non-spam (ham) messages you're receiving. This process will improve the model's accuracy over time, reducing false positives and false negatives.


### Reporting False Positives and False Negatives

Depending on the plugin you're using, there are several ways to report false positives and false negatives to the OOPSpam model:

### API

The API users, should use the Report endpoint documented [here](https://www.oopspam.com/docs/#report) to report any false positives and false negatives. The status of the reported items can be viewed at [the Reported page](https://app.oopspam.com/ReportedSpam) in the OOPSpam Dashboard.

### WordPress

Use [the Form Spam Entries and Form Ham Entries](/wordpress/form-entries/) option to report false positives and false negatives.

### Zapier, Make.com, Bubble.io

1. Set the `Log submissions to OOPSpam` parameter to `true`. For Bubble.io, set `logIt` to `true` in the request body. Refer to [the Spam Detection documentation](https://www.oopspam.com/docs/#spam-detection) for more information on request body parameters.

![OOPSpam Zapier app](screenshot-2.png)

2. This will enable you to view and report all submissions on [the Logs page](https://app.oopspam.com/Logs) in the OOPSpam dashboard. Click __Flag as spam__ or __Flag as ham__ to flag an entry as a false positive or false negative, respectively.

![OOPSpam Logs](screenshot-1.png)

3. The flagged items will be available under [the Reported page](https://app.oopspam.com/ReportedSpam).