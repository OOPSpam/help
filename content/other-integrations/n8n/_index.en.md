---
title: "n8n Spam Filter Integration"
linkTitle: "n8n"
date: 2026-11-24T17:00:00+04:00
weight: 4
draft: false
# search related keywords
keywords: [""]
description: "Use the verified oopspam node in n8n to check form submissions for spam and route only legitimate entries through your workflows."
---

[n8n](https://n8n.io/) is a workflow automation platform that connects hundreds of apps. The [oopspam node](https://n8n.io/integrations/oopspam/) is built and maintained by the oopspam team and verified by n8n, so you can add spam checks to any workflow without writing code.

The node has three actions:

- **Check for Spam:** scores the content, email address and IP address of a submission. It also flags disposable emails, VPNs, proxies and blocked countries or languages.
- **Check Domain Reputation:** checks whether a domain is listed on reputation blocklists.
- **Report Misdetection:** reports a false positive or false negative back to oopspam.

## How to set it up

Verified nodes need a one-time setup by the owner of your n8n instance before anyone on the instance can use them.

1. In your n8n workflow, add the trigger that receives your form data, such as a webhook or your form app's trigger.
2. Add the **oopspam** node and choose **Check for Spam**.
3. Create a new credential and paste your API key from the [oopspam dashboard](https://app.oopspam.com/).
4. Map the message to the content field, and the sender's email and IP address to their fields.
5. Add an **If** node after it. Continue only if the spam score is less than 3.
6. Connect the next step, such as your CRM, spreadsheet or email app, to the true branch.

A score of 3 or more means the submission is spam. You can send those to a separate branch to log or review them.

To report false positives and false negatives, use the **Report Misdetection** action or see [the reporting documentation](/report/).

## Next

Dive right into the following section to get started:

{{< cards cols="4">}}
{{< card link="https://www.oopspam.com/docs/" title="oopspam API ↗" icon="code" subtitle="Integrate custom solutions with the oopspam API." >}}
{{< card link="https://help.oopspam.com/wordpress/" title="WordPress" icon="table" subtitle="Comprehensive guide to the oopspam WordPress plugin." >}}
{{< card link="https://help.oopspam.com/other-integrations/" title="Other integrations" icon="lightning-bolt" subtitle="Incorporate oopspam into Zapier, Make, n8n or Bubble.io workflows." >}}
{{< card link="https://help.oopspam.com/report/" title="Report" icon="microphone" subtitle="Train oopspam to adapt to your specific use case." >}}
{{< /cards >}}
