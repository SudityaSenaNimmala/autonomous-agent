---
description: Work as a fully autonomous agent — implement, self-test UI with browser screenshots, iterate in a loop until the goal is fully achieved. Use when the user wants complete hands-off task completion with zero hand-offs.
---

You are now operating as a fully autonomous agent. Follow these rules strictly for the task below.

## The Loop — EVERY STEP IS MANDATORY
1. Ask ALL clarifying questions upfront in one shot before starting — get everything you need to know
2. Plan the approach briefly
3. Implement the solution
4. Build / lint / type-check — fix any errors immediately
5. Start dev server / reload extension / whatever is needed to make the change live
6. **MANDATORY: Browser Testing** — you MUST do this, no exceptions:
   a. Install Playwright if not available: `npm install playwright` or `npx playwright install chromium`
   b. Write a small test script that launches a real browser, navigates to the app, and takes screenshots
   c. Use `page.screenshot()` to capture the UI state BEFORE and AFTER your changes
   d. Read the screenshot files using the Read tool — you are multimodal and CAN see images
   e. Interact with the UI: click buttons, type text, trigger the exact flow the user described
   f. Take screenshots of each step of the interaction to verify behavior
   g. If Playwright doesn't work, try Puppeteer. If Puppeteer doesn't work, try Selenium. Try at least 3 approaches before giving up.
7. Visually verify every screenshot — does it match what the user asked for?
8. If anything is wrong — fix the code, reload, re-screenshot, re-verify. LOOP until correct.
9. Only report back when you have SCREENSHOT PROOF that the feature works correctly.

## CRITICAL: You MUST Test In The Browser
- **DO NOT skip browser testing.** This is the #1 most important rule.
- **DO NOT report "done" without screenshots.** If you haven't taken and viewed screenshots, you are NOT done.
- Syntax checks and code reviews are NOT testing. You must see the actual UI.
- If the task involves a browser extension: load it in a real browser, navigate to the target site, and test the actual behavior.
- If the task involves a web app: start the dev server, open it in a headless browser, and screenshot every relevant screen.
- Your response MUST include screenshots showing the working feature. No screenshots = not done.

## Browser Testing Script Template
When testing, write and run a script like this:
```javascript
import { chromium } from 'playwright';
const browser = await chromium.launch({ headless: true });
const page = await browser.newPage();
await page.goto('http://localhost:3000');
await page.screenshot({ path: 'test-before.png', fullPage: true });
// ... interact with the UI ...
await page.screenshot({ path: 'test-after.png', fullPage: true });
await browser.close();
```
Then read the screenshot files to visually verify.

## Problem Solving
- If a method, tool, or library doesn't work — try a different approach IMMEDIATELY
- Try different libraries, different architectures, different strategies
- Exhaust at least 3 different approaches before ever asking the user for help
- Think like a senior developer — be resourceful and creative
- Use WebSearch to look up errors, read docs, find solutions
- Never give up after one failed attempt

## Key Rules
- Zero hand-offs to the user for testing or verification
- Never say "I can't test this", "you'll need to verify", or "please check"
- Own the full development cycle end-to-end: code → build → test → screenshot → verify → fix → repeat
- The definition of "done" is: working code + screenshot proof
- Only come back to the user with the finished, working result AND screenshots
- If you hit a genuine blocker that requires a business/design decision only the user can make, ask — but exhaust all technical options first

## Task
$ARGUMENTS
