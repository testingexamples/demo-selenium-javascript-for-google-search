---
name: demo-selenium-javascript-for-google-search
description: Explains the Selenium WebDriver + JavaScript demo written against Google Search's well-known accessible markup to check its home page title, search box, and first result link. Invoke when asked to explain or adapt this demo, or to write a similar real-site Selenium assertion test in JavaScript. Do not use this skill to run the demo against live google.com — see the non-negotiable caution below.
---

# Demo Selenium JavaScript for Google Search

## What this demo teaches

This repo shows real-world Selenium assertion-style testing in JavaScript,
written against a widely-known live site's well-known, publicly documented
markup, with no mocking or fixtures:

1. Load `https://www.google.com` and assert the page title equals exactly
   `Google`.
2. Find the search box via `By.name('q')`, send keys `testing examples`
   followed by `Key.RETURN`, and assert the resulting page title contains
   `testing examples`.
3. Find the first result link via `By.css('#search a')`, click it, and
   assert the browser navigated away from `google.com`.

## ⚠️ Caution: do not run this against live google.com automatically

Google's Terms of Service restrict automated querying of Google Search.
This code is written and reviewed as correct, real `selenium-webdriver`
from first-hand knowledge of Google's markup. It must never be executed
automatically (CI, scheduled jobs, test runners, or any other tooling).
See `README.md` and `AGENTS.md` for the full caution.

## Adapting the pattern to a different real site

1. Pick a real page and note its exact title string.
2. Pick a real search box (or form) and the exact substring you expect in
   the resulting title or body text.
3. Pick a real link on the results and what navigating away should look
   like (e.g. leaving the original domain).
4. Mirror the three-step structure in `src/demo.js`: navigate, assert
   title; search, assert resulting title; click, assert navigation.
5. Update `spec/index.md` (and this skill, if it summarizes the change) to
   match the new site, selectors, and expected strings before changing the
   code.
6. If the target site's Terms of Service allow it, and only then, consider
   whether the resulting demo may be run automatically — this repo's own
   answer for Google Search is no.

---

This skill summarizes the repo. `AGENTS.md` and `spec/index.md` are the
source of truth — if this skill's summary ever disagrees with those, they
win.
