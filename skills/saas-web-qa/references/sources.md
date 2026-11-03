# Sources and integration scope

This skill is an independently written, selective integration of the workflows below, reviewed on 2026-11-04. It does not include or install the original skill packages, their scripts, or their complete guidelines. The local references are usable without fetching the sources; consult the originals when current details or their full coverage are needed.

- [Anthropic webapp-testing](https://github.com/anthropics/skills/tree/main/skills/webapp-testing): browser reconnaissance, rendered-state inspection, and web application verification. The original Python server helper is not included; use the target project's existing setup instead.
- [Vercel web-design-guidelines](https://github.com/vercel-labs/agent-skills/tree/main/skills/web-design-guidelines): UI, usability, interaction and accessibility review. The original fetches current guidelines; this package contains a concise local review guide rather than the complete rule set.
- [Microsoft playwright-cli](https://github.com/microsoft/playwright-cli/tree/main/skills/playwright-cli): browser interaction and automation. This package does not install the CLI or reproduce its command reference.
- [Playwright best practices](https://playwright.dev/docs/best-practices): user-facing locators, test isolation and observable outcomes.
- [W3C WAI preliminary accessibility checks](https://www.w3.org/WAI/test-evaluate/preliminary/): practical checks and the limits of a preliminary assessment.
- [OWASP multi-tenant security](https://cheatsheetseries.owasp.org/cheatsheets/Multi_Tenant_Security_Cheat_Sheet.html) and [authorization testing](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Testing_Automation_Cheat_Sheet.html): role, resource and tenant boundaries; the skill limits checks to the authorized scope and does not assert server enforcement from UI alone.
- [Playwright browser isolation](https://playwright.dev/docs/browser-contexts) and [authentication](https://playwright.dev/docs/auth): browser context isolation and authenticated test state. Separate contexts do not isolate shared server-side data.
- [Playwright accessibility testing](https://playwright.dev/docs/accessibility-testing): automated checks complement rather than replace manual accessibility review.
- [Kimi software testing skills overview](https://www.kimi.ai/ko/resources/software-testing-skills): discovery of testing strategy, browser automation, API checks, defect analysis, and related community projects. Its catalog descriptions are not evidence that those tools were installed or validated here.
- [qa-skills](https://github.com/petrkindlmann/qa-skills): risk-based planning, exploratory testing, API testing, and defect reporting themes.
- [e2e-skills](https://github.com/voidmatcha/e2e-skills): existing E2E test review and failure investigation themes.
- [TestDino playwright-skill](https://github.com/testdino-hq/playwright-skill) and [cypress-agent-skill](https://github.com/KahlilR23/cypress-agent-skill): reuse of the project's browser automation framework and its test practices.
