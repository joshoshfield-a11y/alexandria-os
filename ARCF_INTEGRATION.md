# ARCF Cross-Repo Integration

This document maps how the Alexandria Reality-Contact Framework connects across all repositories in the ecosystem.

## Architecture

```
ALEXANDRIA ECOSYSTEM
│
├── alexandria-os/           ← MASTER GOVERNANCE
│   ├── constitution/        TIG-v2 + ARCF rules + authority matrix + decision tiers
│   ├── registry/schemas/    claim, relation, metric, agent, decision
│   ├── validators/          admission, authority, metric-integrity, drift-reflexivity
│   ├── runtime/             agent templates, pre-mortem gate
│   ├── observability/       dissent channels, traces, drift monitoring
│   └── archive/             rejected claims, failed mappings
│
├── symbiont-ide/            ← SYMBOLIC INTERFACE
│   ├── ArcfOperators.kt     SYM-163-166: governance as first-class operators
│   ├── ArcfValidator.kt     Runtime validation engine (Kotlin)
│   ├── ArcfAuditScreen.kt   Android UI for running audits
│   └── OperatorRegistry.kt  166 operators total (162 + 4 ARCF)
│
├── RGH/                     ← FALSIFICATION PIPELINE
│   ├── validators/admission_validator.py        Chamber1 refactor
│   ├── validators/authority_validator.py        Chamber2 refactor
│   ├── validators/metric_integrity.py           Chamber3 refactor
│   ├── validators/drift_reflexivity.py          Chamber4 refactor
│   └── validators/outcome_auditor.py            Chamber5 (new)
│
└── XANDRIA/                 ← PRODUCTION PLATFORM
    ├── metrics/             5 metric cards with counter-metrics + gaming paths
    └── agents/              Agent constitution for generation pipeline
```

## Integration Points

### 1. symbiont-ide ↔ alexandria-os
- **Schema consumption**: `ArcfValidator.kt` loads YAML schemas from `alexandria-os/registry/schemas/`
- **Operator registration**: `ArcfOperators.ALL` registers SYM-163-166 as native symbolic primitives
- **Lens integration**: `ARCF_AUDIT` lens filters to META category operators for governance review
- **Audit screen**: `ArcfAuditScreen.kt` runs all 4 validators and displays results in Compose UI

### 2. RGH ↔ alexandria-os
- **Schema validation**: All 5 validators load schemas from `../alexandria-os/registry/schemas/`
- **Chamber mapping**:
  - Chamber1 (External Measurement) → `admission_validator.py`
  - Chamber2 (Falsifiability) → `authority_validator.py`
  - Chamber3 (Replication) → `metric_integrity.py`
  - Chamber4 (Cross-domain) → `drift_reflexivity.py`
  - Chamber5 (Outcome) → `outcome_auditor.py` (new)

### 3. XANDRIA ↔ alexandria-os
- **Metric cards**: Each subsystem has a YAML metric record with counter-metrics, gaming paths, off-dashboard audit
- **Agent constitution**: Generation pipeline agent has mandate, non-goals, authority bounds, escalation conditions
- **Pre-mortem**: Required before T2-T4 decisions in release pipeline

## Decision Tier Mapping

| Repo | T0 Creative | T1 Exploratory | T2 Reversible Pilot | T3 Production Assist | T4 Consequential |
|------|-------------|----------------|---------------------|----------------------|------------------|
| **symbiont-ide** | Symbol composition | New operator design | DMT voice mode beta | Accessibility audit | Biometric auth for sync |
| **RGH** | Hypothesis generation | Chamber test design | New validator pilot | CI gate integration | Automated rejection of claims |
| **XANDRIA** | Asset generation | New game mechanic | A/B level test | Player-facing recommendation | Automated release deployment |

## Usage

### Run Admission Check (Python)
```python
from validators.admission_validator import AdmissionValidator
v = AdmissionValidator("../alexandria-os/registry/schemas/")
result = v.validate("claim", {"id": "CLM-001", ...})
```

### Run Authority Check (Kotlin)
```kotlin
val validator = ArcfValidator()
val result = validator.checkAuthority(semantic=3, implementation=4, operational=2, proposedTier="T3")
```

### Audit Metric (Python)
```python
from validators.metric_integrity import MetricIntegrityValidator
v = MetricIntegrityValidator()
result = v.audit(metric_yaml, gaming_min=2, counter_min=1)
```

### Detect Drift (Python)
```python
from validators.drift_reflexivity import DriftValidator
v = DriftValidator()
result = v.detect(current_dist, baseline_dist, sensitivity=0.2)
```

## Next Steps

1. **NEXUS-v4**: Add drift detection to `AudioEngine.ts` for real-time distribution monitoring
2. **UTL-ACS**: Add formal proof validation via `authority_validator` mechanism walk
3. **URCS**: Add fence protocol to kill-switch decisions
4. **Cross-repo sync**: Use `symbiont-ide` GitSyncManager to push ARCF records across all repos
5. **CI integration**: Add admission validator as pre-commit hook in all repos
