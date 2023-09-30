Ubiquitous Language
===================

From [Domain Driven Design](https://www.martinfowler.com/bliki/UbiquitousLanguage.html), I have always liked the idea of writing out how my domain is intended to be used. I don't know if I'm getting it right but this is my try at it. My plan is to move this into a separate doc where it'll evolve as app does.

## Current

Oi is a tool which manage `tasks` assigned to `owners` _identified by their email addresses_. It will create `reminders` for tasks that are not _completed_.

Each `task` consists of a `description`, `owner`, `status`, and _optional_ `note`.
