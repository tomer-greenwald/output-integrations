---
title: Sumologic-Rookout Integration
integration_title: Rookout
kind: integration
git_integration_title: Rookout
---

![logo][rookout-image]

## Setup

### Installation

Rookout sends data to SumoLogic via HTTP POST.

1. Setup a HTTP End point in [Sumologic][sumo-logic-url]
- Login / Register to SumoLogic
- Enter the Setup Wizard
- Enter `Set Up Streaming Data`
- Go to `All Other Sources`
- Select `HTTP Source`
- Configure your `Source Category`

2. Setup [Rookout][rookout-url]

3. Log into [Rookout's webapp][rookout-app-url]

1. In the right panel (Breakpoints) click on the menu button

    ![Breakpoint actions menu](screenshots/click_rule_action.png)

1. Click on *Create new template* in order to edit a new Breakpoint template

    ![Create new template button](screenshots/click_new_template.png)

1. Copy the Sumo Logic Breakpoint template [available here](rule-template.json) into the editor and replace the default Breakpoint template.

    ![SumoLogic Custom Metric Breakpoint template](screenshots/sumologic_template.png)

1. Click the save icon to save the template

    ![Click Save Icon](screenshots/click_save.png)

1. Add the newly created Breakpoint to any application as you would normally !

### Configuration

Once you added the Breakpoint, you can replace the `url` to another SumoLogic endpoint   
Change the `items` dictionary to output any information that you need to send

```json
      {
        "name": "web_hook",
        "target": {
          "url": "https://[SumoEndpoint]/receiver/v1/http/[UniqueHTTPCollectorCode]"
        },
        "items": {
          "function": "store.rookout.frame.function",
          "filename": "store.rookout.frame.filename",
          "line": "store.rookout.frame.line",
          "locals": "store.rookout.frame.locals",
          "variables": "store.rookout.variables"
        }
      }
```

## Troubleshooting
If you have any questions, contact us at support@rookout.com.

## Further Reading
Find out more at [https://docs.rookout.com][rookout-docs]

[rookout-image]: logos/avatars-bot.png
[rookout-url]: https://docs.rookout.com/docs/getting-started.html
[rookout-docs]: https://docs.rookout.com/
[rookout-app-url]: https://app.rookout.com
[sumo-logic-url]: https://www.sumologic.com/