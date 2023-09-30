---
tags: [ron-jeffries, mmmss, ubiquitous-language]
---
Initial commit
==============

This project has two purposes: 

1. to build a tool that will help me at work 
2. to show my development process and how I think about the decisions I'm making while building. 

It's heavily inspired by [Ron Jeffries' blog series][ron-blog] on building [a game engine that handles Asteroids and Space invaders.][ron-game] Where he has been showing his thought process and steps taken to build the game. 

[ron-blog]: https://ronjeffries.com/articles/-y023/python/-a250/254/
[ron-game]: https://github.com/RonJeffries/python-asteroids-1

Why Oi? It's about getting someone else's attention, and it's an exclamation used by the British. Apparently mostly angry, but, the tool is here to help us avoid anger. And it's only two letters long so that's nice.

## To show my development process

I work with a lot of developers and often reference certain blog posts, conference talks, and more from various developers that have inspired me. But I don't have a good reference project, or code, to show them what it looks like together. And to me, the code is only part of the story, how it came to be is also important and the mindset I have. Which, really, is all about taking [Many More Much Smaller Steps][mmmss] while looking towards an end-goal and keep my options open.

[mmmss]: https://github.com/RonJeffries/python-asteroids-1

## The tool

I work at a fairly large company and I often have to help introduce changes across many different teams. And I'm far from alone. Tracking spreadsheets are the way, but they are a lot of manual work. I need to inform people (hopefully they read that email, Slack message, etc.) but invariably you'll end up chasing people. On bigger projects or rollouts you're likely chasing for status updates.

So, as a first stab I want to build a tool that given a Google Sheet can:

1. Look up whom the owner is
2. See their current status (done or not)
3. Whether they have filled in all the information we've requested of them
4. Create reminders to those who are not done

This is a good MVP and would make my life a lot simpler. In a later version I'd probably want to be able to have more statuses (configurable), maybe some validation of the inputs (although, I can probably leave that to the sheet…), some kind of web interface for configuring the current _information gathering project_ I have, and of course deadlines, checkin intervals, and so on.

### information gathering project

I don't know what the term for each piece of work the tool will have. Is it a project? Overall it's about gathering information, but that's a bit of a mouthful. Project feels like an overloaded term but also definitionally `project` might be the term I want:

> pro•ject [noun]  
> an individual or collaborative enterprise that is carefully planned to achieve a particular aim

## What will be in the MVP?

To iterate quickly and show that I have something useful I want a CLI. While I want to work with Google Sheets in the end I will start by reading CSV files. For a couple of reasons:

- It will allow me to work offline
- Super simple to iterate on and I can export any current sheet to CSV while beta testing
- Any more advanced concept that Google Sheets may give me I still need to model in my domain, so if I need to understand how it would work if I don't have that one tool
  - So I could also work with Excel or some other spreadsheet/database like tool. To understand what _the minimum_ thing I need is. And how to extend it to something nicer.
- It is also a good showcase for hexagonal architecture or ports and adapters
  - Where I want to talk about _what my domain_ cares about and not what Google Sheets find important

Then, there is some way I expect information to be provided to me. Since I know checkboxes show up as `TRUE` or `FALSE` in the CSV export of a sheet I'll start there. If I expect some input I'll accept anything that isn't a blank string (i.e. not only whitespace). I bet this will have to be expanded. But also, the point of this is that it's a human that _needs_ this information, so they'll be doing manual validation, too. And most important: the person I need information from. If I have an email I can look them up on Slack and I can send an email which are both my most common methods of getting in touch with someone, so I'll just start with only supporting email for the owner. 

That highlights another assumption: Either all sheets are the same or I need configuration. Since it's a CLI tool and I need to work on something I think it's fair to assume I'll need either some parameters passed in or a config.  
I'll start with some parameters, and probably I'll extend it to a config file.

Creating reminders is a bit vague and that's because I don't want the MVP to integrate with Slack or email. I have scripts already that can people on Slack (using AppleScript) if I have their email, so I'll reuse it.

## First stab at a ubiquitous language

From [Domain Driven Design](https://www.martinfowler.com/bliki/UbiquitousLanguage.html), I have always liked the idea of writing out how my domain is intended to be used. I don't know if I'm getting it right but this is my try at it. My plan is to move this into a separate doc where it'll evolve as app does.

> Oi is a tool which manage `tasks` assigned to `owners` _identified by their email addresses_. It will create `reminders` for tasks that are not _completed_.
> 
> Each `task` consists of a `description`, `owner`, `status`, and _optional_ `note`.
