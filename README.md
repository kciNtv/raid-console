# Raid Reminder Console

A single-page settings GUI for the (private) **RaidHelperReminder** bot repo.
Live at: **https://kcintv.github.io/raid-console/**

## What it is

`config.json` in the bot repo controls everything the bot does. This page is a
friendly editor for that file: teams, channel routing, reminder cadence,
message wording, announcements, report channels. Clicking **Save & deploy**
commits the change — which *is* the deployment; the next scheduled run uses it.
It can also trigger a **dry run** (a test run that sends nothing and logs who
*would* be messaged).

## How it works (and why it's safe to host publicly)

- This repo contains **only code** — no server, no database, no guild data,
  no secrets. All settings stay in the private bot repo.
- The page runs entirely in your browser and talks only to `api.github.com`
  using a **fine-grained personal access token** you create, scoped to the one
  bot repo with just `Contents: read/write` + `Actions: read/write`.
- The token is stored in your own browser's localStorage and never leaves it
  except to GitHub. "Sign out" deletes it. Anyone without such a token sees an
  empty sign-in page — there is nothing else here.
- Token creation is walked through step-by-step on the page itself.

## After ownership transfer

The sign-in screen lets you change the repo owner/name — so when the bot repo
is transferred to a new owner, they point the console at their copy and create
their own token. Nothing in this repo needs to change (except this README's
links, if the console repo is transferred too).

## Development

One file: `index.html`. No build step, no dependencies. Edit, commit, Pages
redeploys.
