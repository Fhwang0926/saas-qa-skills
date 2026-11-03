---
name: saas-web-qa
description: Review and investigate website or SaaS quality through browser exploration, simulated user journeys, UI and accessibility reviews, API checks, and existing test evidence. Use for web QA, reproducing user-facing bugs, or persona-based usability reviews.
---

# SaaS web QA

Use this skill for the requested website, user journey, or changed UI. Follow the user's instructions, the target project's rules, and the tool provider's instructions first. The bundled references contain adapted guidance; no other skill installation or network fetch is required to read them.

## Workflow

1. Establish the target, environment, requested journeys, authentication and account role, and any restrictions. Include logged-in product journeys when requested; reaching the dashboard alone is not success if the requested goal is inside the application. Inspect the existing application and relevant project guidance before choosing a tool. Use the running application if available; start a local process only when needed and allowed. Use `localhost` for local URLs when the project or user requires it.
2. Select the smallest useful checks for the request. Read [browser QA](references/browser-qa.md) for live exploration or automation, [UI and accessibility](references/ui-accessibility.md) for visual, interaction, and accessibility reviews, and [QA planning and diagnosis](references/qa-planning.md) when reviewing authenticated SaaS roles or workspaces, planning coverage, inspecting API behavior, or investigating existing test failures. Use the relevant references together when needed. A source-only review is not proof of live behavior.
   When the user requests persona-based QA, simulated users, or a multi-agent user-journey review, read [persona journeys](references/persona-journeys.md) and follow its delegation, evidence, consolidation, and recheck workflow. Use the other references as relevant.
3. Inspect the rendered page and its state before interacting. Check the expected user-visible result, including relevant loading, empty, error, and responsive states. Prefer the existing browser tools and installed dependencies. Follow project instructions on whether builds, automated tests, server starts, or code changes are allowed.
4. Protect real users and data. Do not expose secrets, credentials, session data, or personal data in evidence. Do not submit payments, send messages, delete data, change permissions, or otherwise cause consequential side effects without authorization. Treat database access as read-only when required by the user or project. Do not claim an unexecuted check passed.
5. If fixes are requested or otherwise authorized, investigate and implement the in-scope fixes while preserving unrelated changes. Recheck the original behavior in the same environment when the running application has picked up the change; follow user and project restrictions on tests, builds, process starts and data. If rechecking is not possible, report why rather than treating a source edit as runtime verification. For persona-based work, follow the more specific consolidation and rerun procedure in [persona journeys](references/persona-journeys.md).
6. Report reproducible findings first: environment, page/state, steps, expected and actual behavior, and supporting evidence or source location. For persona-based work, use the frequency and severity reporting in its reference; otherwise order findings by impact. Separate observed failures, source-based risks, and unverified areas. State what was changed, what was checked and what could not be checked. Do not assert WCAG conformance from a partial review.

For the upstream sources and scope of the adaptations, see [sources](references/sources.md).
