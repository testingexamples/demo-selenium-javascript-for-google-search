# Spec: Demo Selenium JavaScript for Google Search

## Summary

This repo is a beginner-friendly walkthrough of Selenium WebDriver browser
automation in JavaScript. `src/demo.js` is written as real, correct
`selenium-webdriver` code targeting the well-known, publicly documented
markup of <https://www.google.com>, and demonstrates three real,
assertion-based checks. Because Google's Terms of Service restrict
automated querying of Google Search, this code is not run against the live
site by this repo's own tooling, and must never be run automatically.

## Scope

This spec covers only the three test scenarios implemented in
`src/demo.js`. It does not cover unrelated Google Search features, other
browsers, or other Google products.

## Principles and rules

* All three checks are written as real assertions, matching the shape they
  would take if run against the live, real google.com — there is no
  mocking, stubbing, or fixture data standing in for a fake site. What
  makes this repo different from demo-selenium-javascript-for-nhs-wales is
  not the code's realism, but that this code must never actually be
  executed against the live site automatically (see AGENTS.md).
* The demo uses the `selenium-webdriver` package's Chrome driver directly
  (via `Builder().forBrowser(Browser.CHROME)`), not a wrapper or test
  framework.
* Expected strings and selectors must be matched exactly as written below
  and in the source.
* If the code (`src/demo.js`) and this file ever disagree, that is a defect
  in one of them; fix it before doing anything else.

## Detail

1. **Home page title check**
   * Navigate to: `https://www.google.com`
   * Get the page title.
   * Assert the title equals exactly: `Google`

2. **Search box check**
   * Find the search input via `By.name('q')`.
   * Google's search input has historically been a plain
     `<input name="q">`; Google has since migrated it to a
     `<textarea name="q">` (an autosize textarea styled to look like a
     single-line input). The `name="q"` locator has remained stable across
     that drift.
   * Send keys: `testing examples` followed by `Key.RETURN`.
   * Get the resulting page title.
   * Assert the title contains the substring: `testing examples`

3. **First result link check**
   * Find the first result link via `By.css('#search a')`.
   * Note: the exact DOM structure of a Google results page (container
     ids, class names, nesting) shifts over time as Google ships
     redesigns, so this selector is a reasonable, documented best guess
     rather than a guaranteed-stable contract.
   * Click the link.
   * Get the current URL.
   * Assert the current URL does not contain the substring: `google.com`
     (i.e. the browser navigated away from Google).

## Acceptance criteria

* `src/demo.js` is syntactically correct JavaScript and matches this spec
  exactly (selectors, strings, and assertions as written above). This repo
  does not require, and must never attempt, a passing live run against
  google.com as an acceptance criterion — see AGENTS.md for why.

## Related topics

* [../README.md](../README.md)
* [../AGENTS.md](../AGENTS.md)

## Sources

* <https://www.google.com>
* <https://www.google.com/policies/terms/>
* <https://testingexamples.github.io/examples/google-search/>
