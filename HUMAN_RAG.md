# Human RAG — Cognitive Legacy Engine

> The core innovation behind VRAXIA.

---

## The Problem

Every year, companies lose what made them great.

When a senior professional leaves, their judgment leaves too — their reasoning patterns, their heuristics, their institutional memory. No document captures it. No onboarding transfers it. No traditional system preserves it.

**The real competitive advantage of an organization lives in the minds of its people.**

---

## Traditional RAG vs Human RAG

| | Traditional RAG | Human RAG |
|---|---|---|
| **Input** | Documents, PDFs, wikis | Conversations, decisions, reasoning sessions |
| **What it captures** | Facts and text | Patterns of judgment and reasoning |
| **Granularity** | Document-level | Expert-level cognitive chunks |
| **Knowledge type** | Explicit | Tacit + explicit |
| **Context** | Static | Living, evolving |
| **Output** | Text fragments | Calibrated reasoning response |

---

## Core Concept

```
Traditional RAG:
  query → search documents → return text fragment

Human RAG:
  query → search cognitive chunks → retrieve reasoning patterns
        → apply psychological profile → generate calibrated response
```

The output is not just "what the expert knows."  
The output is "how the expert would reason about this."

---

## The Pipeline

### Phase 1 — Capture

Conversational sessions with the professional. The system extracts:

- Decision patterns with confidence scores
- Reasoning heuristics and mental models
- Exception handling logic ("when I would NOT follow the rule")
- Domain-specific judgment frameworks

**The goal is not to record facts. The goal is to capture how the expert thinks.**

### Phase 2 — Distillation

Extracted patterns are converted into `CognitiveChunks`:

- Two independent embeddings per chunk: semantic (content) and contextual (domain + content)
- Stored in pgvector with dual-index for hybrid retrieval
- Confidence scoring for each pattern
- Metadata: domain, context, temporal weight, source session

### Phase 3 — Psychological Profiling (PsychAgent)

This is what separates Human RAG from every other knowledge system.

PsychAgent conducts a 20-exchange conversational assessment applying 6 simultaneous instruments:

| Instrument | What it measures |
|---|---|
| **Big Five NEO-PI-R** | Personality structure |
| **CRT Adapted** | Cognitive reflection / analytical vs. intuitive style |
| **Schwartz Values Survey** | Core values and motivational priorities |
| **BEI STAR Protocol** | Behavioral competency patterns |
| **AT-20 Inferred** | Tolerance for ambiguity |
| **Cognitive Bias Mapping** | Active biases (HIGH/MEDIUM/LOW) |

The result is a `PsychologicalProfile` JSON that calibrates every aspect of knowledge generation:

```
PsychologicalProfile {
  bigFive:         { openness, conscientiousness, extraversion,
                     agreeableness, neuroticism }
  decisionStyle:   "analytical" | "intuitive" | "hybrid"
  riskProfile:     "averse" | "neutral" | "seeking"
  crtScore:        number  // 0–7
  ambiguityScore:  number  // 0–100
  activeValues:    string[]
  biasAlerts:      { bias: string, severity: "LOW"|"MEDIUM"|"HIGH" }[]
}
```

### Phase 4 — Calibrated Retrieval + Generation

At query time:

1. Query is vectorized
2. Top-K cognitive chunks retrieved by cosine similarity
3. `buildCalibratedPrompt()` injects the full psychological profile into the generation context
4. LLM generates a response as the professional would — including their real limitations, known biases, and decision style

**The response is not "what the AI thinks."  
It is "what Carlos Ribeiro would say, thinking the way Carlos Ribeiro thinks."**

---

## Cognitive Legacy

Human RAG is positioned as a **Cognitive Legacy** product.

> *"Preserve and scale the judgment of exceptional professionals — so their knowledge never disappears when they leave."*

The four outcomes:

1. **Preserve expert reasoning** — not just documents
2. **Accelerate onboarding** — new hires query the cognitive twin of predecessors
3. **Reduce critical knowledge loss** — expertise is institutionalized, not personalized
4. **Create living organizational memory** — continuously updated as professionals evolve

---

## PsychAgent

PsychAgent is the psychological profiling engine inside Human RAG.

**It does not require a human psychologist.**  
**It does not require the professional to know they are being assessed.**  
**It runs entirely via conversational AI.**

Cost per full psychological assessment: **R$ 0.00** (local LLM)  
Time to complete: **< 2 hours**  
Consistency across assessments: **100%**

Compare to traditional psychological assessment:
- Cost: R$ 4.000+ per session
- Time: 3–5 business days
- Consistency: ~60% (inter-rater variability)

---

## Why This Matters

The implications go beyond HR or knowledge management:

- **For CTOs**: a semantic layer of institutional expertise accessible via API
- **For HR leaders**: onboarding that transfers the judgment of the best, not just the process documentation
- **For Legal**: contract reasoning calibrated by the reasoning style of your senior counsel
- **For Investors**: a defensible moat — proprietary cognitive profiles are not replicable

---

> Human RAG is the differentiating layer that makes VRAXIA more than an AI platform.  
> It is what makes VRAXIA a **Cognitive Legacy System.**
