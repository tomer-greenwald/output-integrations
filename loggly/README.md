---
title: Loggly-Rookout Integration
integration_title: Rookout
kind: integration
git_integration_title: Rookout
---

![logo][rookout-image]

## Setup

### Installation

Rookout sends data to Loggly via a HTTP Webhook.

1. Get a Customer Token from Loggly [see their docs](loggly-token-docs-url)

2. Setup [Rookout][rookout-url]

3. Log into [Rookout's webapp][rookout-app-url]

1. In the right panel (Breakpoints) click on the menu button

    ![Breakpoint actions menu](screenshots/click_rule_action.png)

1. Click on *Create new template* in order to edit a new Breakpoint template

    ![Create new template button](screenshots/click_new_template.png)

1. Copy the Loggly Breakpoint template [available here](rule-template.json) into the editor and replace the default Breakpoint template.


1. Click the save icon to save the template

    ![Click Save Icon](screenshots/click_save.png)

1. Add the newly created Breakpoint to any application as you would normally !

### Configuration

Once you added the Breakpoint, you can replace the `url` to another Loggly endpoint  
Change the `items` dictionary to output any information that you need to send

```json
"operations": [
      {
        "name": "web_hook",
        "target": {
          "url": "http://logs-01.loggly.com/inputs/<YOUR_TOKEN>/tag/http/"
        },
        "items": {
          "function": "store.rookout.frame.function",
          "filename": "store.rookout.frame.filename",
          "line": "store.rookout.frame.line",
          "locals": "store.rookout.frame.locals",
          "variables": "store.rookout.variables"
        }
      }
    ]
```

## Troubleshooting
If you have any questions, contact us at support@rookout.com.

## Further Reading
Find out more at [https://docs.rookout.com][rookout-docs]

[rookout-image]: logos/avatars-bot.png
[rookout-url]: https://docs.rookout.com/docs/getting-started.html
[rookout-docs]: https://docs.rookout.com/
[rookout-app-url]: https://app.rookout.com
[loggly-token-docs-url]: https://www.loggly.com/docs/customer-token-authentication-token/
