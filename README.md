# Playwright MCP Jupiter

This repository contains Playwright-based UI automation for the Jupiter Toys sample application, plus a smaller set of root-level Playwright experiments.

## Repository layout

| Path | Purpose |
| --- | --- |
| `jupiter-toys/e2e/` | Primary Jupiter Toys end-to-end framework built with Playwright, TypeScript, Page Object Model (POM), and Allure reporting |
| `tests/` | Root-level sample Playwright tests created outside the main Jupiter Toys framework |
| `.github/workflows/playwright.yml` | GitHub Actions workflow for the root Playwright setup |

If you want to run the Jupiter Toys automation suite, use `jupiter-toys/e2e`.

## Primary framework

The main automation project lives in `jupiter-toys/e2e` and includes:

- Playwright with TypeScript
- Page Object Model classes under `pages/`
- Cross-browser execution for Chromium, Firefox, and WebKit
- HTML and Allure reporting
- Screenshot utilities for test evidence
- Jupiter Toys coverage for home, contact, and login flows

## Project structure

```text
Playwright_MCP_Jupiter/
|- .github/
|  '- workflows/
|     '- playwright.yml
|- jupiter-toys/
|  '- e2e/
|     |- pages/
|     |  |- basePage.ts
|     |  |- cartPage.ts
|     |  |- contactPage.ts
|     |  |- homePage.ts
|     |  |- locators.ts
|     |  '- loginPage.ts
|     |- test/
|     |  |- contact.spec.ts
|     |  |- home.spec.ts
|     |  |- login.spec.ts
|     |  '- validLogin.spec.ts
|     |- utils/
|     |  |- allureUtil.ts
|     |  '- screenshotUtil.ts
|     |- ALLURE_GUIDE.md
|     |- README.md
|     |- package.json
|     |- playwright.config.ts
|     '- tsconfig.json
|- tests/
|  |- example.spec.ts
|  |- launchBrowser.spec.ts
|  |- sample.spec.ts
|  '- samplelogin.spec.ts
|- package.json
|- playwright.config.ts
'- tsconfig.json
```

## Prerequisites

- Node.js
- npm

## Quick start

Run the main Jupiter Toys suite from the repository root or from `jupiter-toys/e2e`:

```bash
git clone https://github.com/MamillaVenkatKiran/Playwright_MCP_Jupiter.git
cd Playwright_MCP_Jupiter\jupiter-toys\e2e
npm install
npx playwright install
npm run test
```

The root `npm` test scripts delegate to the nested framework, so the suite can also be run from `Playwright_MCP_Jupiter` after installing both package directories.

## Available scripts

From `jupiter-toys/e2e` (or use the equivalent root script):

```bash
npm run test
npm run test:headed
npm run test:ui
npm run test:debug
npm run test:chromium
npm run test:firefox
npm run test:webkit
npm run allure:report
npm run allure:show
```

## Test target

The Jupiter Toys framework is configured to run against:

```text
https://jupiter.cloud.planittesting.com/#/
```

## What is covered today

Current coverage in `jupiter-toys/e2e/test` includes:

- home page title verification
- login workflow checks
- higher-priority login coverage scenarios
- contact form interaction coverage

Supporting page objects also exist for cart interactions.

## Reporting

The main framework writes:

- Playwright HTML reports
- Allure results and generated reports
- screenshots captured by utility helpers

For Allure usage details, see `jupiter-toys/e2e/ALLURE_GUIDE.md`.

## Notes

- The nested `jupiter-toys/e2e/README.md` contains framework-specific details.
- Some sample tests currently use illustrative credentials in code. Move sensitive or environment-specific data to configuration before using the suite in shared environments.
- The root-level Playwright setup is separate from the main Jupiter Toys POM framework.
