# Screenshots & Platform Visuals

> Live platform: [vraxia-platform.vercel.app](https://vraxia-platform.vercel.app)

---

## Platform Overview

The VRAXIA platform UI is a dark-theme, observability-first dashboard with five core views:

### 1. Visão Geral (Overview)

The main dashboard shows:
- Active professionals enrolled in Human RAG
- Cognitive chunks indexed (with average confidence score)
- Active specialized agents
- Monthly query volume and average latency
- Live activity feed — real-time queries being processed by cognitive twins
- Human RAG pipeline status: Capture → Distillation → PsychAgent → Twin → Agents

### 2. PsychAgent

Psychological assessment engine view:
- Completed sessions counter
- Cost per session: **R$ 0.00** (local LLM)
- Average exchanges per session
- Big Five radar chart (sample mean across enrolled professionals)
- Instrument coverage rates (Big Five, CRT, Schwartz, BEI, AT-20, Bias Mapping)
- Individual professional profile — full Big Five breakdown with bar charts
- Active cognitive bias alerts (HIGH / MEDIUM / LOW severity)

### 3. Agentes VRAXIA

Agent ecosystem view:
- Human RAG Engine as backbone visualization
- 6 operational agents: Commercial, HR, Legal, Operations, Finance, CX
- Each agent: domain, function description, active status indicator
- Architecture diagram showing Human RAG as the central intelligence layer

### 4. Pipeline RAG

Technical pipeline view:
- Phase 1: Capture (LLaMA 3.1 8B · local)
- Phase 2: Distillation (text-embedding-3-small · dual embedding)
- Phase 3: Psychological Assessment (LLaMA 3.1 70B · PsychAgent)
- Phase 4: Retrieval + Calibrated Generation (GPT-4o-mini)
- Local-first stack: Ollama + PostgreSQL/pgvector + Redis

### 5. Métricas (Business Metrics)

Business and unit economics view:
- Gross margin: > 97%
- Setup fee per enterprise
- Monthly recurring revenue per enterprise
- 12-month revenue projection chart (stacked bar: setup fees + recurring)
- Competitive comparison: VRAXIA vs traditional human assessment
  - Cost: -98%
  - Delivery time: -99%
  - Consistency: +100%
- Investment allocation breakdown (Product / GTM / Infra / Operations)

---

## Design System

| Element | Value |
|---|---|
| Background | `#0A0A0A` |
| Surface | `#111111` |
| Primary accent | `#C8A96A` (gold) |
| Typography | Times New Roman (headers) + Courier New (monospace data) |
| Tone | Premium · Institutional · Precision instrument |

---

## Live Demo

→ **[vraxia-platform.vercel.app](https://vraxia-platform.vercel.app)**

The live platform includes all five views with real interface interactions, Chart.js visualizations, and navigation between modules.

---

> Screenshots directory: `docs/screenshots/` *(to be added)*
