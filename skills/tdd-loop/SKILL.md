
---
name: tdd-loop
description: >
  Automate the full test-driven development cycle with a collaborative agent team.
  Use when the user asks to run the TDD loop, implement this feature with TDD,
  write tests and implement, evolve this code, TDD this feature, or provides
  a feature description or failing tests and wants autonomous test-driven implementation.
  Also triggers on red green refactor, test-first development, or parallel TDD.
metadata:
  version: "1.0.0"
---

# Test-Driven Evolutionary Loop

Orchestrate a team of agents to implement features through test-driven development.
Two coder agents work in parallel on isolated files while a devil advocate agent
challenges their implementations.

## Entry Points

### Mode 1: Feature Description
1. Analyze the feature description and the existing codebase
2. Write comprehensive failing tests first
3. Run tests to confirm they fail (red phase)
4. Proceed to agent dispatch

### Mode 2: Existing Failing Tests
1. Read and analyze the failing tests
2. Run them to confirm current failure state
3. Identify the target module/file
4. Proceed to agent dispatch

## Agent Dispatch

Create variant files: module_variant_a.py and module_variant_b.py
Launch Coder A, Coder B in parallel, and Devil Advocate simultaneously.

## Convergence

- Both pass: pick the stronger one per devil advocate review
- One passes: use it, check for critical concerns first
- Neither passes: synthesize best parts, retry up to 3 times

## Promotion

1. Copy winning variant into the original module file
2. Run full test suite to confirm
3. Clean up all variant and review files
4. Report results
