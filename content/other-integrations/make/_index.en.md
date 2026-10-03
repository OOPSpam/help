---
title: "Make"
date: 2024-10-31T11:02:05+06:00
weight: 3
draft: false
# search related keywords
keywords: [""]
---

[Make](https://www.make.com/en?utm_source=oopspam&utm_medium=partner&utm_campaign=oopspam-partner-program) is a visual automation platform that lets you send information between oopspam API and thousands of apps with just a few clicks. All you have to do is drop [oopspam Make App](https://www.make.com/en/integrations/oopspam-anti-spam) to your scenario and enter API key.

Let's look at the following example.

!["Contact Form 7 integrates with oopspam Anti-Spam on Make"](OOPSpamApp-Integromat.png)

On this scenario, we add and connect Contact Form 7, oopspam Anti-Spam and Airtable apps.

1. Contact Form 7 app receives form submissions and passes data to oopspam app.
2. oopspam analyzes and passes the spam score to the filter between oopspam and Airtable app.
3. Filter allows data to be passed to Airtable app only if the spam score is less than 3.
4. Airtable receives data and insert it to a spreadsheet.
5. ✅ Done!

!["Airtable spreadsheet"](airtable-cf7.png)

Every contact form, comment, email and chat apps on Make can be connect in similar fashion.

To report false positives and false negatives, see [the reporting documentation](/report).

### Related blog posts:

- [Stop Spam on Elementor Forms Using Make and oopspam](https://www.oopspam.com/blog/elementor-form-make-spam)
- [Stop Spam on Breakdance Forms Using Make and oopspam](https://www.oopspam.com/blog/stop-spam-on-breakdance-forms-using-make-and-oopspam)

## Next

Dive right into the following section to get started:

{{< cards cols="4">}}
{{< card link="https://www.oopspam.com/docs/" title="oopspam API ↗" icon="code" subtitle="Integrate custom solutions with the oopspam API." >}}
{{< card link="https://help.oopspam.com/wordpress" title="WordPress" icon="table" subtitle="Comprehensive guide to the oopspam WordPress plugin." >}}
{{< card link="https://help.oopspam.com/other-integrations" title="Other integrations" icon="lightning-bolt" subtitle="Incorporate oopspam into Zapier, Make, or Bubble.io workflows." >}}
{{< card link="https://help.oopspam.com/report" title="Report" icon="microphone" subtitle="Train oopspam to adapt to your specific use case." >}}
{{< /cards >}}