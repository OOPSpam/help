---
title: "Account"
breadcrumbs: false
date: 2025-07-16T11:02:05+06:00
icon: "ti-user"
description: "Learn how to manage your account."
type : "docs"
weight: 5
---

## Where is my API Key?

You can find your API key in the top right corner of the dashboard's main page, located under the "Your API key" section.

![Your API key](your-api-key.png)

## How do I rotate my API key?

You can now rotate your OOPSpam API key yourself — no need to contact support.

**Where to find it:** Account Settings → API Key (or go directly to [https://app.oopspam.com/Identity/Account/Manage/ApiKey](https://app.oopspam.com/Identity/Account/Manage/ApiKey)).

**What it does:** Generates a new API key and immediately invalidates the old one. Use this if your key has been accidentally exposed or you're rotating credentials as a security practice.

![Rotate your API key](rotate-api-key.png)

A few things to know:

- Available on all paid plans.
- Limited to **3 rotations per calendar year** (the counter resets on January 1st).
- The old key stops working instantly — make sure to update it everywhere you use it.

## How to upgrade or downgrade, cancel?

### Upgrading and downgrading

If you're using the Free plan, clicking any Upgrade link will redirect you to the pricing page on your dashboard. Simply select your desired plan, click the upgrade button, and enter your payment details. Your account will be upgraded within seconds.

![Upgrade](upgrade.png)

For users on paid plans, locate the "Manage your subscription" link in your dashboard. This takes you to the subscription management page where you can switch plans by clicking the "Move here" button under your desired plan. This action will upgrade or downgrade your account depending on the selected plan.

![Upgrade to a different plan](move-here.png)

{{< callout type="info" >}}
You can switch to an Annual plan on this page for additional savings.
{{< /callout >}}

### Canceling

To cancel your subscription, navigate to the "Manage your subscription" page and click the Cancel button under your current plan.

![Cancel](cancel.png)

When canceling, you'll have the option to **pause the cancellation**. Pausing keeps your current plan active and lets you continue using it until your next billing period, instead of canceling right away.

{{< callout type="alert" >}}
🚨 **IMPORTANT** If you proceed with the cancellation, your account immediately reverts to the Free plan.
{{< /callout >}}

## How to update my billing information?

Navigate to the "Manage your subscription" page and click the "Update payment details" link to open the billing information window.

![Update billing information](update-billing-info.png)

{{< callout type="info" >}}
Keep your billing information current and ensure sufficient funds are available. After three failed payment attempts (with ~5 day intervals), the system will restrict your API key. We'll notify you via email after each attempt, giving you time to update your billing information. Access remains restricted until valid payment details are provided.
{{< /callout >}}

### Where are the invoices?

Access your receipts through the Account page. From the dashboard, navigate to Account → Receipts.

![Invoices](invoices.png)


## Next

Dive right into the following section to get started:

{{< cards cols="4">}}
{{< card link="https://www.oopspam.com/docs/" title="OOPSpam API ↗" icon="code" subtitle="Integrate custom solutions with the OOPSpam API." >}}
{{< card link="https://help.oopspam.com/wordpress" title="WordPress" icon="table" subtitle="Comprehensive guide to the OOPSpam WordPress plugin." >}}
{{< card link="https://help.oopspam.com/other-integrations" title="Other integrations" icon="lightning-bolt" subtitle="Incorporate OOPSpam into Zapier, Make, or Bubble.io workflows." >}}
{{< card link="https://help.oopspam.com/report" title="Report" icon="microphone" subtitle="Train OOPSpam to adapt to your specific use case." >}}
{{< /cards >}}