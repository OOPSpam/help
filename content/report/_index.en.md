---
title: "Reporting"
breadcrumbs: false
date: 2024-10-21T11:02:05+06:00
icon: "ti-agenda"
description: "Learn how to report false positives and false negatives"
type : "docs"
weight: 4
---

The OOPSpam API takes an optimistic approach and avoids blocking messages unless it's confident they are spam. However, false positives (legitimate messages marked as spam) and false negatives (spam messages marked as legitimate) can still occur.
There are various reasons for false positives and false negatives, such as:

- IP addresses previously used for spamming but now in different hands, retaining a bad reputation.
- Messages incorrectly flagged

To minimize these occurrences, it's essential to train the OOPSpam API's standard model with the specific spam and non-spam (ham) messages you're receiving. This process will improve the model's accuracy over time, reducing false positives and false negatives.


## Reporting False Positives and False Negatives

Depending on the plugin (or the API) you're using, there are several ways to report false positives and false negatives to the OOPSpam model:

### API

The API users, should use [the Report endpoint](https://www.oopspam.com/docs/#report) to report any false positives and false negatives. The status of the reported items can be viewed at [the Reported page](https://app.oopspam.com/ReportedSpam) in the OOPSpam Dashboard.


{{< callout type="info" >}}
To report via the OOPSpam Dashboard, add the [`logIt`](https://www.oopspam.com/docs/#spam-detection) parameter in the request body to view and report requests on [the Logs page](/wordpress/form-entries/#logs-in-the-oopspam-dashboard).
{{< /callout >}}

### WordPress

Use [the Form Spam Entries and Form Ham Entries](/wordpress/form-entries/) tables to report false positives and false negatives.

### Zapier, Make.com, Bubble.io

1. Set the `Log submissions to OOPSpam` setting to `true`. For Bubble.io, set `logIt` to `true` in the request body.

    ![OOPSpam Zapier app](screenshot-2.png)

2. This will enable you to view and report all submissions on [the Logs page](https://app.oopspam.com/Logs) in the OOPSpam dashboard. Click __Flag as spam__ or __Flag as ham__ to flag an entry as a false positive or false negative, respectively.

    ![OOPSpam Logs](screenshot-1.png)

3. The flagged items will be available under [the Reported page](https://app.oopspam.com/ReportedSpam).


## Next

Dive right into the following section to get started:

{{< cards cols="4">}}
{{< card link="https://www.oopspam.com/docs/" title="OOPSpam API ↗" icon="code" subtitle="Integrate custom solutions with the OOPSpam API." >}}
{{< card link="https://help.oopspam.com/wordpress" title="WordPress" icon="table" subtitle="Comprehensive guide to the OOPSpam WordPress plugin." >}}
{{< card link="https://help.oopspam.com/other-integrations" title="Other integrations" icon="lightning-bolt" subtitle="Incorporate OOPSpam into Zapier, Make, or Bubble.io workflows." >}}
{{< card link="https://help.oopspam.com/report" title="Report" icon="microphone" subtitle="Train OOPSpam to adapt to your specific use case." >}}
{{< /cards >}}