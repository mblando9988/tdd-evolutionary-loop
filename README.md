# TDD Evolutionary Loop

A Claude Code plugin that runs test-driven development on Python code with
three agents. Two coder agents write competing versions of the same module in
separate files while a reviewer agent looks for bugs and missed edge cases. The
version that passes the tests and the review replaces the original file.

## Steps

1. You describe a feature or point it at failing tests.
2. If you gave a description, it writes the tests first and confirms they fail.
3. Two coder agents work at the same time, each in its own copy of the file,
   and the reviewer runs alongside them.
4. The better passing version is copied into the real file and the full test
   suite runs again.
5. The extra copies are deleted.

If neither version passes, it combines the best parts of both and tries again,
up to 3 times.

## Use

Start it with a feature:

    TDD loop: add a caching layer to the user service that expires after 5 minutes

Or with tests you already have:

    TDD loop: make all the tests in tests/test_parser.py pass

"Implement this with TDD", "red green refactor" and "parallel TDD" start it too.

## Limits

Two coders, each allowed up to 10 tries (see
`skills/tdd-loop/references/workflow-details.md`), and up to 3 combine-and-retry
rounds. These are fixed in the skill files, not settings.

Tests run with pytest.
