# Alexa Skill to display Lovelace dashboards on Echo Show

This Alexa skill adds a voice command to open Lovelace dashboards on the Echo Show in the built-in Silk browser.

> [!IMPORTANT]
> **This is a fork from https://github.com/aldadic so thank you for his amazing work.**

The original project involves passing a URL and the page number to display. In this fork, the idea is that the URL is fixed, we always call the Home Assistant URL, and it will ask us for a username and password. We can change the Dashboard by assigning one to each user, without touching the skill URL or asking the user for extra data.

## How it works

Let's assume your Home Assistant URL is ``http://homeassistant.local:8123``. Home Assistant dashboard URLs then have the following structure:

```html
http://homeassistant.local:8123/
```

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
