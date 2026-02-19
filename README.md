# 🤖 VSCODE AGENTS 🤖

This repository focus on TDD agents for Python projects, providing a structured workflow for writing tests, implementing features, and refactoring code while maintaining high quality standards.

## Changelog
- v0.0.1 - Initial commit with TDD agents for Red, Green, and Refactor phases following the TDD cycle based on lineal chain (Red -> Green -> Refactor -> Red).
- v1.0.0 - Added detailed workflows for each TDD phase, including tool usage and shared state management via `.tdd_memory.md`. 

## Agents Overview (as of v1.0.0)
### TDD Supervisor Agent
- Orchestrates the TDD cycle, ensuring proper handoffs between Red, Green, and Refactor agents based on the current status in `.tdd_memory.md`.
### TDD Red Agent
- Writes failing tests based on requirements using uv and pytest.
### TDD Green Agent
- Implements minimal code to make the test pass while ensuring code quality.
### TDD Refactor Agent
- Refactors code while maintaining passing tests and strict linting standards.
### Shared State Management
- All agents read from and write to `.tdd_memory.md` to maintain a single source of truth regarding the current status, features, errors, modified files, and linting status.

## Pre-requisites
Property `chat.customAgentInSubagent.enabled` must be set to true in vscode settings to allow agents to call other agents as part of the TDD cycle.

## Usage
You only need to interact with the TDD Supervisor agent. It will manage the workflow and handoffs between the Red, Green, and Refactor agents based on the current status in `.tdd_memory.md`.

Sample prompts to the TDD Supervisor:
- "I want to start a new feature for PDF processing (splitting and OCR). Please guide me through the TDD cycle."

## Troubleshooting
If you get this message: 

```
Copilot has been working on this problem for a while. It can continue to iterate, or you can send a new message to refine your prompt. Configure max requests.
```

You will need to set chat.agent.maxRequests to a higher number in your vscode settings.