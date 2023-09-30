Oi
==

_Oi is developed as a blog, see [the Devlog.](./docs/devlog/)_

## Why
I work at a fairly large company and I often have to help introduce changes across many different teams. And I'm far from alone. Tracking spreadsheets are the way, but they are a lot of manual work. I need to inform people (hopefully they read that email, Slack message, etc.) but invariably you'll end up chasing people. On bigger projects or rollouts you're likely chasing for status updates.

## What
So, as a first stab I want to build a tool that given a Google Sheet can:

1. Look up whom the owner is
2. See their current status (done or not)
3. Whether they have filled in all the information we've requested of them
4. Create reminders to those who are not done

This is a good MVP and would make my life a lot simpler. In a later version I'd probably want to be able to have more statuses (configurable), maybe some validation of the inputs (although, I can probably leave that to the sheet…), some kind of web interface for configuring the current _information gathering project_ I have, and of course deadlines, checkin intervals, and so on.

## How

A CLI tool that works on CSV files in a fixed format that creates an output file which can be read by other scripts to send reminders to task owners.
