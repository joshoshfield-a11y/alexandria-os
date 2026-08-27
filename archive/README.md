# archive/

Storage for rejected claims, failed mappings, retired controls,
and invalidated experiments.

## Principle

A failed relation is not dead weight. It is a boundary marker that
prevents future agents from repeating a beautiful but invalid translation.

## Structure

```
archive/
├── rejected-claims/        # Claims that failed admission or were falsified
├── failed-mappings/        # Cross-domain relations that broke under test
├── retired-controls/       # Safeguards removed after fence review
├── invalidated-metrics/    # Metrics that became targets and corrupted
├── deprecated-agents/      # Agents that exceeded authority or misaligned
└── experiment-failures/    # Experiments that did not replicate
```

## Retention Policy

- Permanent retention for all archived records
- Immutable — never delete, only append deprecation notices
- Searchable by future agents to prevent repeated failures
- Include full reasoning for rejection/retirement
