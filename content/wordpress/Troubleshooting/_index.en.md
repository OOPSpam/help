---
title: "Troubleshooting"
date: 2024-10-21T11:02:05+06:00
weight: 5
draft: false
# search related keywords
keywords: ["warning"]
---

If your question about this or any other topic is not answered here, please reach out to our support team for assistance. We are always happy to help.

### Form submissions on my WordPress websites are being flagged as spam.

If your form has a textarea field (usually this field is used for longer form fields like message) and it is not a required field (or can be less than 20 characters) in your form then make sure you uncheck the "Consider short messages as spam" setting in the OOPSpam WordPress plugin settings. This setting will prevent form submissions if a textarea field in your form is too short to be considered a meaningful sentence.

Another setting to pay attention to is the sensitivity level setting. Make sure it is set to recommended level 3.

If all the above settings are configured correctly, please use [Form Spam Entries](https://www.oopspam.com/help/wordpress/form-entries/) to report false positives. The system will quickly adapt to your use case and you will likely not have this issue.

### I'm a paid customer but I see warning about API limit

If you're experiencing an API limit warning on your WordPress dashboard, please follow these steps to resolve the issue:

1. Confirm that you have a valid API key. Make sure that you have registered on the [OOPSpam Dashboard](https://app.oopspam.com) and copied the key.
2. Paste the API key into _My API Key_ in the OOPSpam WordPress Settings.
3. Select _OOPSpam Dashboard_ from _I got my API Key from_
4. Check _Activate Spam Protection_ for the contact form plugin you have.
5. Wait for the first form or comment submission to come in.
6. The API usage numbers will be updated with each submission and the warning will be removed.