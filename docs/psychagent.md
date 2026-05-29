# PsychAgent

> Cognitive and behavioral profiling through AI. No human psychologist required.

---

## What PsychAgent Does

PsychAgent conducts a structured 20-exchange conversational assessment that applies six psychological instruments simultaneously — invisibly, through natural conversation.

The output is a `PsychologicalProfile` that calibrates how VRAXIA's agents reason on behalf of each professional.

---

## The Six Instruments

| Instrument | Domain | What it captures |
|---|---|---|
| **Big Five NEO-PI-R** | Personality | Openness, conscientiousness, extraversion, agreeableness, neuroticism |
| **CRT Adapted** | Cognition | Analytical vs. intuitive decision style (0–7 score) |
| **Schwartz Values Survey** | Values | Core motivational priorities and value hierarchy |
| **BEI STAR Protocol** | Behavior | Behavioral event patterns in high-stakes situations |
| **AT-20 Inferred** | Tolerance | Ambiguity tolerance score (0–100) |
| **Cognitive Bias Mapping** | Biases | Active biases with severity (LOW / MEDIUM / HIGH) |

---

## Output Structure

```
PsychologicalProfile
├── bigFive
│   ├── openness:          72
│   ├── conscientiousness: 88
│   ├── extraversion:      41
│   ├── agreeableness:     58
│   └── neuroticism:       34
├── decisionStyle:         "analytical"
├── riskProfile:           "averse"
├── crtScore:              6
├── ambiguityScore:        61
├── activeValues:          ["security", "achievement", "tradition"]
└── biasAlerts
    ├── { bias: "confirmation", severity: "HIGH" }
    └── { bias: "anchoring",   severity: "MEDIUM" }
```

---

## How It Calibrates Generation

When a query arrives for a professional's cognitive twin:

1. Retrieve Top-K cognitive chunks (reasoning patterns)
2. Build calibrated prompt with full `PsychologicalProfile`
3. Inject active biases as generation constraints
4. Generate response that reflects:
   - The professional's analytical style
   - Their risk tolerance
   - Their known cognitive biases (so they can be surfaced, not hidden)
   - Their value-driven decision priorities

---

## Why It Matters

| Traditional Assessment | PsychAgent |
|---|---|
| R$ 3.000–8.000 per session | R$ 0.00 (local LLM) |
| 3–5 business days | < 2 hours |
| Human inter-rater variability ~60% | 100% consistent |
| One-time snapshot | Refreshable over time |
| Requires trained psychologist | Fully autonomous |

---

## Ethical Boundaries

PsychAgent is designed with clear ethical constraints:

- **Not for surveillance** — profiles are used to scale expertise, not to monitor employees
- **Not deterministic** — profiles calibrate reasoning tendency, not fixed behavior
- **Consent-aware** — enterprise deployment requires organizational consent frameworks
- **Bias transparency** — active biases are surfaced, not hidden or amplified
