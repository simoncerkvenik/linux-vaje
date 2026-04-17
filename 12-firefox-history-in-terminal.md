# Reading Firefox History from the Terminal on Linux

Today I explored how to read Firefox browsing history directly from the terminal in Linux.

## What I learned
- `history` shows terminal command history
- `ps aux` shows running processes
- Firefox browsing history is stored in an SQLite database called `places.sqlite`

## Finding the Firefox profile
First, I checked the Firefox profiles directory:

```bash
ls ~/.mozilla/firefox
```

In my case, the profile was:
```bash
0scq17w.default-release
```

## Copying the database

Because Firefox may keep the database locked
while running, I first created a copy:
```bash
cp ~/.mozilla/firefox/0scvq17w.default-release/places.sqlite
/tmp/ffhistory.sqlite
```

## Reading the browsing history

Then I used `sqlite3` to query the copied database:
```bash
sqlite3 /tmp/ffhistory.sqlite "SELECT url, title, datetime(last_visit_
date/1000000,'unixepoch','localtime') FROM moz_places ORDER BY last_visit_date DESC LIMIT 20;"
```

## Why this matters

This helped me understand the difference between:

- terminal command history
- running processes
- browser history
- application data stored in Linux

## Key takeaway

Linux troubleshooting becomes much easier when you know:

- where applications store their data
- how to inspect files from the terminal
- how to use basic SQLite queries to extract useful information

