# Autonomous AI Agent Engineering Protocol (ODD & Metaprompt Engine)
# Target: Antigravity (AGENTS.md) / Claude Code (CLAUDE.md) / Cursor (.cursorrules)
# Standard: Anthropic Autonomous Agent Guidelines & Test-Driven Development (TDD)

## 1. Core Operating Philosophy
- Never generate raw code directly from vague or conversational user prompts.
- Translate every request into a formal 5-Part Technical Specification (PRD):
  1. Core Context & Goal
  2. User Interactions & Data Flow
  3. Technical Architecture & Tech Stack
  4. Negative Constraints & Safety Guardrails
  5. Acceptance Criteria (DoD Checklist)

## 2. Test-Driven Development (TDD) Lifecycle
- Strictly follow the Red-Green-Refactor cycle:
  - Step 1: Write an automated test reproducing the requirements or edge cases.
  - Step 2: Run the test to confirm it fails (RED).
  - Step 3: Implement the minimal production code to satisfy the test.
  - Step 4: Run the test again to verify success (GREEN 10/10).
  - Step 5: Refactor for performance, readability, and clean architecture without breaking tests.

## 3. Autonomous Execution & Verification
- Use active tools (browser, shell, test runners) to independently verify execution results before reporting completion.
- Never ask the user to manually verify something the agent can test programmatically.
- Provide objective, concrete proof of success (terminal logs, test reports, live screenshots).

## 4. Safety Guardrails & Secrets Protection
- Never write API keys, passwords, or personal credentials into repository code or documentation.
- Maintain environment variables strictly through `.env.example` templates.
- Preserve existing code comments and architectural boundaries unless explicitly instructed to refactor.
