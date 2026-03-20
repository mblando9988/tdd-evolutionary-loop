# TDD Evolutionary Loop

Automate test-driven development with a collaborative agent team. Two coder agents implement features in parallel on isolated files while a devil's advocate agent reviews their work.

## Why Use This Plugin?

Traditional TDD is powerful but slow. This plugin accelerates the cycle by running multiple implementation attempts in parallel and adding an adversarial review layer that catches issues tests alone miss.

## How It Works

1. You describe a feature (or point to failing tests)
2. Tests are written automatically if starting from a description
3. Two coder agents work simultaneously on isolated variant files
4. A devil's advocate reviews both implementations for edge cases, bugs, and code quality issues
5. The best implementation wins and gets promoted to the main file
6. Cleanup removes all temporary variant files

## Quick Start

Describe a feature:
TDD loop: add a caching layer to the user service that expires after 5 minutes

Or point to existing tests:
TDD loop: make all the tests in tests/test_parser.py pass

You can also say implement this feature with TDD, red green refactor, or parallel TDD to trigger the skill.

## Configuration

| Parameter | Default | Description |
|-----------|---------|-------------|
| Number of coders | 2 | Parallel implementation agents |
| Max iterations | 10 | Attempts per coder before giving up |
| Max convergence | 3 | Synthesis retries when no variant passes |

## Supported Frameworks

The skill auto-detects pytest or unittest from your project configuration. Defaults to pytest if no signals are found.
