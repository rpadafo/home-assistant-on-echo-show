# Alexa Skill to display Lovelace dashboards on Echo Show

This Alexa skill adds a voice command to open Lovelace dashboards on the Echo Show in the built-in Silk browser.

> [!IMPORTANT]
> **This is a fork from https://github.com/aldadic so thank you for your amazing work.**

> [!NOTE]
> The original project requires a URL, a dashboard name, and a number that we assign to the Home Assistant view. In this fork, we removed the dashboard name and view number so that Alexa always opens the main URL. This way, Alexa will not ask for any additional information, and we can control the Dashboard that opens with Home Assistant users (assigning a dashboard to each user).

## How it works

When the skill is invoked, it uses the [OpenURL](https://developer.amazon.com/en-US/docs/alexa/alexa-presentation-language/apl-standard-commands-v1-5.html#open_url_command) APL command to open the page

```html
http://homeassistant.local:8123/
```

in the Silk browser on the Echo Show.

## Installation

For instructions how to set this skill up refer to the [installation](INSTALLATION.md) page.

## How to use

Once you've set this skill up refer to the [usage](USAGE.md) page for details how to use this skill effectively.

## TODO

* Make it possible to import this skill via GitHub URL to simplify installation.
