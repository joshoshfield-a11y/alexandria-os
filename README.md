# Alexandria OS

The master governance layer for the Alexandria ecosystem.

## What This Is

Alexandria OS is not an operating system in the traditional sense. It is a **governance runtime** that ensures claims, metrics, agents, and decisions across all projects remain grounded in evidence rather than compelling language.

## Seven Layers

| Layer | Purpose | Files |
|-------|---------|-------|
| **constitution/** | Non-negotiable policy | TIG-v2, ARCF-rules, authority matrix, decision tiers |
| **registry/schemas/** | Typed record schemas | claim, relation, metric, agent, decision |
| **validators/** | Deterministic checks | admission, authority, metric-integrity, drift-reflexivity |
| **runtime/** | Operational templates | agent constitution, pre-mortem gate |
| **observability/** | Traces and dissent | dissent channels, anomaly states, drift monitoring |
| **archive/** | Failed mappings | rejected claims, retired controls, experiment failures |
| **ARCF_INTEGRATION.md** | Cross-repo map | How all repositories connect to this governance layer |

## Quick Start

```bash
# Validate a claim
python -c "
from validators.admission_validator import AdmissionValidator
v = AdmissionValidator('registry/schemas/')
print(v.validate('claim', {'id': 'CLM-001', ...}))
"

# Check authority
python -c "
from validators.authority_validator import AuthorityValidator
v = AuthorityValidator()
print(v.check(3, 4, 2, 'T3'))
"
```

## Ecosystem

- **symbiont-ide**: Symbolic interface where ARCF is operable as first-class nodes (SYM-163-166)
- **RGH**: Empirical validation arm — 5 chambers refactored to ARCF validators
- **XANDRIA**: Production platform with metric cards and agent constitutions
- **NEXUS-v4**: Real-time engine with drift detection
- **UTL-ACS**: Formal proof system (pending integration)
- **URCS**: Safety architecture (pending integration)

## Governing Rule

> Nothing becomes architecture because it is compelling. It becomes architecture only when its registry record specifies what it is, what it preserves, what would falsify it, who independently checks it, what authority it earns, and how it can be reversed.
