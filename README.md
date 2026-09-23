# TDD Evolutionary Loop

A Claude Code plugin that runs test-driven development with three agents. Two
coder agents write competing versions of the same code in separate files, and a
reviewer agent checks both for bugs and missed edge cases. The version that
passes the tests and the review replaces the original file.

## Steps

1. You describe a feature or point it at failing tests.
2. If you gave a description, it writes the tests first and confirms they fail.
3. Two coder agents work at the same time, each in its own copy of the file.
4. The reviewer checks both versions.
5. The better passing version is copied into the real file and the full test
   suite runs again.
6. The extra copies are deleted.

If neither version passes, it combines the best parts of both and tries again,
up to 3 times.

## Use

Start it with a feature:

    TDD loop: add a caching layer to the user service that expires after 5 minutes

Or with tests you already have:

    TDD loop: make all the tests in tests/test_parser.py pass

"Implement this with TDD", "red green refactor" and "parallel TDD" start it too.

## Settings

| Setting | Default | Meaning |
|---------|---------|---------|
| Number of coders | 2 | Coder agents running at once |
| Max iterations | 10 | Tries per coder before it stops |
| Max convergence | 3 | Retries when neither version passes |

## Test frameworks

Picks pytest or unittest based on the project's config. Uses pytest if it
can't tell.
