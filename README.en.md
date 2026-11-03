# SaaS Web QA Skill

[한국어](README.md) | English | [日本語](README.ja.md) | [Tiếng Việt](README.vi.md) | [Español](README.es.md) | [Português](README.pt.md) | [Français](README.fr.md) | [Deutsch](README.de.md) | [Italiano](README.it.md)

A single skill for reviewing website and SaaS behavior, responsive interfaces, and accessibility. It selectively adapts workflows from public Anthropic, Vercel, Microsoft, and other QA skills. The instructions and checklists are bundled; the original skills and their tools are not installed.

Depending on the request, it can also help plan risk-based QA, inspect API behavior, review existing Playwright or Cypress tests, and investigate failures. See [sources and scope](skills/saas-web-qa/references/sources.md).

Authenticated reviews account for the authorized role and workspace, relevant lists and filters, and the scope of any persistence check. Parallel browser sessions may still share server-side data.

For persona-based QA, ten simulated users explore the journey in a real browser, including authenticated features using authorized sessions. When supported, separate subagents collect findings and screenshots; requested fixes are followed by the same journeys again. See [persona journeys](skills/saas-web-qa/references/persona-journeys.md).

## QA workflow

- **Diagnose, fix, and recheck:** For both ordinary and persona-based QA, requested fixes are made within scope and the original behavior is rechecked once the running service has picked up the change. If rechecking is not possible, report why and what remains unverified.
- **Separate journeys:** When multiple features are requested, define an entry point and success criterion for each. Persona-based QA records results per journey and, for each issue, the number of personas able to evaluate the step and the number affected. Findings are ordered by frequency, with severe issues highlighted separately.
- **Before and after login:** If login is blocked but an authorized session already exists, authenticated features can be checked separately. Do not report an uninterrupted end-to-end success.

## Public QA skills and practices incorporated

The workflows below were selectively adapted into one `saas-web-qa` skill. The original packages, complete rules, scripts, and tools are not bundled or installed. See [sources](skills/saas-web-qa/references/sources.md) for links and scope.

| Public skill or collection | Practice incorporated |
| --- | --- |
| Anthropic `webapp-testing` | Inspect rendered pages before checking user actions and outcomes. |
| Vercel `web-design-guidelines` | Review UI, usability, interaction, and accessibility. |
| Microsoft `playwright-cli` | Browser interaction and automation workflows. |
| `qa-skills` | Risk-based planning, exploratory QA, API checks, and defect reporting. |
| `e2e-skills` | Review existing E2E test quality and investigate failures. |
| TestDino `playwright-skill` | Browser testing using the project's existing Playwright setup. |
| `cypress-agent-skill` | Browser testing using the project's existing Cypress setup. |

## Ask an agent to install and run it

Give your coding agent a request like this. The repository must be published on GitHub and accessible to the agent.

```text
Install the saas-web-qa skill from https://github.com/Fhwang0926/saas-qa-skills
in the current project, read its instructions, and perform the QA below.
If it is already installed, check that it supports the requested task before using it.

Target: the current project's login page
Scope: desktop and mobile layout, login behavior, and accessibility
```

For installation only, request installation without asking for QA. An agent may need a new session to discover the skill; if it can read the installed files, it can follow them in the same session.

### Instructions for agents

1. Identify the target project and agent, and read the user's and project's instructions. If `saas-web-qa` is installed, read its `SKILL.md` and relevant references and verify they support the requested task; do not assume the name means it is current. Reuse it if sufficient. Otherwise, inspect the accessible source in this repository and the installed source and local changes; update according to user and project rules without overwriting work that cannot safely be replaced. If updating is unsafe, use the accessible source instructions directly where possible. Report missing features or inaccessible sources and do not claim the installation is current without evidence.
2. If installation is needed, run the command below in the target project. If interactive selection is unavailable and the agent is known, select only that agent; for Codex, add `--agent codex -y`. Do not add `-g` unless global installation was requested. Follow the environment's installation and tool rules.
3. Check the installation result and path, then read `SKILL.md` and the relevant `references/`. If the skill is not registered in the current session but its files are readable, follow them directly. Do not perform QA when only installation was requested.
4. Prefer the running service and available browser. Follow user and project rules for builds, tests, starting servers, databases, and external services. If tools or access are missing, report the blocker and completed scope; do not claim installation or QA succeeded without evidence.

## Install directly

After the repository is published, run this once in the target project. Node.js 22.20 or later is required; select your agent when prompted.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

To install from a local checkout, replace the path below with its actual location:

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Installation is project-scoped by default. Add `-g` for global installation. Restart the agent if needed for discovery.

## Usage

```text
$saas-web-qa Review the login page on desktop and mobile and report reproducible issues.
```

### Diagnose, fix, and recheck in one request

```text
$saas-web-qa Review the running service as ten simulated user personas.
Use separate subagents where possible, and check the public pages and core
authenticated features with an authorized account in a real browser.
Capture screenshots of confusion or blockers and report, for each issue,
how many personas reached the step and how many encountered the problem.
Fix the confirmed issues together, repeat the journeys under comparable
conditions, and report what was resolved and what remains.
```

The skill supplies instructions, not a browser, Playwright, a running application, or accounts. Live checks require the appropriate environment and access. User and project rules take precedence.
