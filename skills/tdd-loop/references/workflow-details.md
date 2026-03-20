
# Workflow Details

## Shared Artifacts
- Test file: read-only for all agents
- Variant files: each coder owns exactly one
- Review file: written by devil advocate, read by orchestrator

## Test Execution Strategies

Strategy 1 - Symlink swap:
  cp module.py module_backup.py
  cp module_variant_a.py module.py
  python -m pytest tests/test_module.py
  cp module_backup.py module.py

Strategy 2 - PYTHONPATH manipulation:
  Create a temp directory with the variant renamed to the original module name.

Strategy 3 - Importlib patching:
  Use a conftest.py fixture that patches the import.

## Configuration Defaults

| Parameter | Default | Description |
|-----------|---------|-------------|
| Number of coders | 2 | Parallel implementation agents |
| Max iterations per coder | 10 | Red-green cycles before giving up |
| Max convergence attempts | 3 | Synthesis retries when no variant passes |
| Devil advocate count | 1 | Always exactly one reviewer |
