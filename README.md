# Table Football Scoreboard

A shared, real-time scoreboard for office table football. Tracks individual rankings across 1v1 and 2v2 matches. Built as a single HTML file with no framework or build step. Data is stored in Firebase Firestore and syncs live across all devices.

## Features

- Individual leaderboard — points are tracked per player, not per team
- Supports both 1v1 and 2v2 matches
- Weekly leaderboard reset every Sunday at 23:59 CET, with full match history preserved
- Real-time sync — any match recorded by one person appears instantly for everyone else
- Add and remove players from a shared pool
- Match history grouped by week

## Scoring

| Result | Points |
|---|---|
| Win | 3 |
| Win by more than 5 goals | 4 |
| 10-0 (perfect game) | 5 |
| Loss | 0 |

Maximum score per game is 10. At least one team must reach 10 for a result to be valid.

## How to use

Open the URL in any browser. No login required.

- **Leaderboard** — current week's individual standings
- **Add Match** — select players, enter score, submit
- **History** — all matches ever recorded, grouped by week
- **Players** — add or remove players from the dropdown pool

## Tech

- Plain HTML, CSS, and JavaScript — no build step, no dependencies
- [Firebase Firestore](https://firebase.google.com/docs/firestore) for real-time shared storage
- Firebase loaded via CDN (`gstatic.com/firebasejs`)
- Hosted on GitHub Pages

## Firebase setup

This app connects to a Firestore database. The config is hardcoded in `index.html`.

Firestore rules are currently set to test mode (`allow read, write: if true`). This is fine for a small internal group. If you want to lock it down, update the rules in the [Firebase console](https://console.firebase.google.com) under Firestore → Rules before the test mode expiry.

## Local development

No build step needed. Just open `index.html` in a browser. It will connect to the same Firestore database as the hosted version.

## Weekly reset

The leaderboard resets automatically each Monday (detecting the boundary at Sunday 23:59 CET). All match history is kept — only the points calculation resets to the current week. A manual reset option is available in the Players tab.
