---
description: 'Use these guidelines when generating or updating tests.'
applyTo: tests/**
---
# [Project Name] Testing Guidelines

## Stack & Tools
- **Runner**: `pytest`
- **Environment**: `uv` (execute commands via `uv run ...`)
- **Linting & Formatting**: `ruff`
- **Mocks**: `pytest-mock`(preferred) or `unittest.mock`

## Code Style
- **Formatting**: All code must be formatted. Run `uv run ruff format .`
- **Linting**: Code must pass linting. Run `uv run ruff check .`
- **Type Hints**: Use standard Python type hints strictly.

## Test Conventions
1.  **Isolation**: Tests must not depend on DB state or network unless tagged as integration.
2.  **Naming**: `test_<verb>_<noun>_<condition>` or descriptive sentences.
3.  **AAA Pattern**: Explicitly comment `# Arrange`, `# Act`, `# Assert` in complex tests.
4.  **Minimalism**: Test behavior, not implementation details.

## Failure Standards
- A test is strictly "Red" only if it produces an `AssertionError`.
- `ImportError`, `NameError`, or `SyntaxError` are implementation gaps (or invalid tests), not valid test failures.

## Manage Dependencies
- Use `pytest-mock` for mocking when possible.
- Avoid complex fixtures that obscure test intent.
- If needed, create simple fixtures in `conftest.py` with clear names.
- Dont add real dependencies unless necessary. If needed use uv add to install them, not modify uv.lock or pyproject.toml directly.