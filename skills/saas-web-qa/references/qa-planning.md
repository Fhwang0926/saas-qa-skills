# QA planning and diagnosis

This guide selectively adapts themes from the QA and E2E skills cited in [sources](sources.md). Apply it only to the requested website and scope; use the target project's existing requirements and tools.

## Risk-based coverage

- Identify the changed or requested journeys, affected user roles and environments, and the expected behavior from available requirements. Prioritize cases by user impact and likelihood, including loss of access, incorrect data, and interruption of a core journey. Label inferred expectations and unresolved requirements.
- For each important journey, select meaningful normal, boundary, permission-denied and failure cases. Include relevant loading, retry, empty and recovery states. Use a compact list of scenario, preconditions, action and expected result when a plan is requested; record cases not exercised.
- Reuse existing smoke or regression coverage when applicable. Distinguish a proposed case from a case actually run and its observed outcome; do not infer coverage from a test's name or a passing status alone.

## SaaS roles and workspace context

- For an in-scope authenticated journey, note the account role, workspace, subscription or feature availability that actually applies, and the expected allowed or unavailable actions. If multiple roles or workspaces are relevant, map the requested journey against the authorized accounts and environments that are actually available; mark unavailable combinations unverified rather than assuming coverage.
- When the user has authorized access to multiple test workspaces, check the visible workspace context and the relevant in-scope data after navigating or switching normally. A browser context isolates browser state, not server-side account data or shared resources. Do not access another tenant's data, alter identifiers, impersonate another role, or perform active authorization probing without an explicitly authorized scope and suitable test accounts.
- A hidden or disabled control alone does not prove server-side authorization. Only report the behavior observed for the authorized role; distinguish it from server enforcement or tenant isolation that has not been verified. Do not change permissions, plans or shared settings solely to manufacture a scenario.

## API and integrations

- When in scope and permitted, inspect the actual request and response for the affected journey: method, endpoint, status, relevant response fields, validation and visible error handling. Correlate browser and API evidence without logging credentials, private data or full sensitive payloads. A successful status alone does not prove the intended business effect.
- Prefer safe read-only checks against an authorized environment. Never reset, initialize or modify a database when user or project instructions restrict it to reads. Do not perform state-changing requests or send third-party messages simply to improve coverage. Record when payment, email, authentication or other integrations were mocked or could not be exercised.

## Existing automated tests

- If test review or debugging is requested, inspect the existing Playwright, Cypress or other framework configuration, relevant tests and available failure artifacts before proposing changes. Preserve the project's conventions; do not introduce another framework merely to use this skill.
- Look for tests that can pass without verifying the intended behavior, conditional or skipped assertions, overly broad mocks, shared state, fixed delays, brittle selectors and assumptions about execution order. Connect each concern to its effect on the reported result.
- For intermittent failures, compare the available failure evidence and distinguish an application defect from timing, data, environment, or third-party dependency hypotheses. Do not call an issue flaky based on a single failure; do not increase retries as a substitute for diagnosis. Run tests only if user and project instructions permit it.

Performance or security reviews beyond the requested web QA require an explicit scope and appropriate authorization. Do not launch load tests or active security scans by default.
