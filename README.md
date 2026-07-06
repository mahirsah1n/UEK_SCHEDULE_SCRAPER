# UEK Schedule Scraper

A Python scraper that logs into USOSweb (UEK's student information system) and turns my class schedule into a calendar file (.ics) — so it syncs into Google Calendar, Apple Calendar, or any app that reads .ics, instead of me checking USOSweb every time.

## Why I built this

USOSweb doesn't offer calendar sync, and checking it manually every week for schedule changes got old fast. I wanted my classes to just show up wherever I already keep my calendar.

## What it does

- Logs into USOSweb and navigates to the schedule page (Selenium, to handle authentication and dynamic content)
- Parses the schedule with BeautifulSoup
- Exports the parsed schedule as a calendar file (.ics)
- Saves a raw copy of the scraped schedule as CSV for reference

## Stack

Python, Selenium, BeautifulSoup, Requests

## A note on security

An earlier version of this had USOSweb login credentials committed in plaintext. I found it, removed it from the codebase, and rotated the credentials. Never commit credentials directly — this one's a mistake I made once and won't make again.

## Setup

​```bash
pip install -r requirements.txt
​```

Update the USOSweb credentials at the top of `apollo_scraper.ipynb` with your own before running (do not commit them). Then run the notebooks in order:
1. `apollo_scraper.ipynb` — scrapes and saves the schedule
2. `calendar_export.ipynb` — converts it into a `.ics` file

Sample outputs are in `schedules/` and `calendars/`.
