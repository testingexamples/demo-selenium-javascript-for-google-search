# AGENTS.md

This repo is a small, beginner-friendly walkthrough (`src/demo.js`) that uses
Selenium WebDriver in JavaScript to demonstrate real, assertion-based checks
against Google Search's well-known, publicly documented markup at
<https://www.google.com>.

## Source of truth

`spec/index.md` is the single source of truth for the exact three assertions
and selectors this demo describes. If `src/demo.js` and `spec/index.md` ever
disagree, that is a defect in one of them — fix it before doing anything
else.

## Install and run

See `README.md` for Install and Run steps, including chromedriver
troubleshooting (macOS Gatekeeper quarantine blocks, and Chrome/chromedriver
version-mismatch errors). Do not duplicate those instructions here; follow
the README.

## Non-negotiable: never run this against live google.com automatically

Google's Terms of Service restrict automated querying of Google Search.
Unlike this org's demo-selenium-javascript and
demo-selenium-javascript-for-nhs-wales repos — which target sites their
authors intend the demo to actually be run against, including in CI — this
repo's `src/demo.js` must never be executed against the live google.com by
CI, a scheduled job, a test runner, or any other automated tooling, in this
repo or elsewhere. The code is written and reviewed as correct, real
`selenium-webdriver` from first-hand knowledge of Google's markup; it is
not validated by a live run here, and it must stay that way. Do not add a
CI workflow, test hook, or script that executes this file automatically.

Do not change the target site, the three test scenarios, or the exact
expected strings (title, search term, selectors) without first updating
`spec/index.md` to match.

---

CLAUDE.md is a pointer to this file — it is the single source of truth for
agent instructions.
