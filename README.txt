# StudySprint Web

StudySprint turns a list of study tasks into a timed session. You add subjects and tasks, choose what to study today, set minutes for each task, and the app runs the timer with breaks in between.

This repository is the web version of the StudySprint Android app. It has the same features, the same theme and the same scheduling rules.

**Live site:** https://dhruvv-x.github.io/studysprint-web/

## Features

- Subjects and tasks, with a priority of low, medium or high
- Session planner with minutes per task and optional breaks between tasks
- Pause, resume and skip during a session
- A heads-up when the planned time is reached, with the option to keep going
- Timer based on saved timestamps, so the time stays correct after a refresh or a closed tab
- Session history and analytics for the last 7 or 30 days
- Daily goal in minutes, shown on the home screen
- Light and dark theme, following the system or set manually
- Works offline, no account needed

## Scheduling rules

The planning logic is plain rule-based code with no network calls.

- **Breaks:** only placed between tasks, never before the first or after the last one.
- **Overrun:** if a task runs over, the next break shrinks by half of the extra time. It never goes below half its planned length or 1 minute.
- **Quick skip:** skipping a task within the first minute removes the break after it.
- **Early finish:** finishing a minute or more early shortens the rest of the session.
- **Suggestions:** after a task has been completed twice, the app suggests the average time you actually took.

## Project structure

```
index.html        Landing page
app/index.html    The web app
```

Both files are self-contained. There is no build step and no dependency to install.

## Run locally

Download or clone the repository and open `index.html` in a browser. No server is needed.

```
git clone https://github.com/dhruvv-x/studysprint-web.git
```

## Data storage

All data is saved in the browser's localStorage under the key `studysprint-v1`. Nothing is sent to a server. This means:

- Data stays on the device and browser where it was created.
- Clearing site data or using a private window removes it.
- The hosted site and a local copy keep separate data.

## Tech

HTML, CSS and vanilla JavaScript. The Android version is built with Kotlin, Jetpack Compose, Room and DataStore.

## Author

Dhruv ([@dhruvv-x](https://github.com/dhruvv-x))
