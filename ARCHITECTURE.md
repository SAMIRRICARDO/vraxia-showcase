# Architecture Overview

> Conceptual system design. No implementation details are exposed.

---

## System Layers

```
┌─────────────────────────────────────────────────────────────────┐
│                        VRAXIA Platform                           │
│                                                                 │
│  ┌─────────────────┬──────────────────┬───────────────────────┐ │
│  │  Specialized    │   Human RAG      │      PsychAgent       │ │
│  │  Agents (8)     │   Engine         │      Cognitive        │ │
│  │                 │                  │      Profiling        │ │
│  └────────┬────────┴────────┬─────────┴──────────┬────────────┘ │
│           │                 │                    │              │
│  ┌────────▼─────────────────▼────────────────────▼────────────┐ │
│  │              Multi-Agent Orchestration Layer               │ │
│  │         Planner · Orchestrator · Evaluator                 │ │
│  └────────────────────────┬───────────────────────────────────┘ │
│                           │                                     │
│  ┌────────────────────────▼───────────────────────────────────┐ │
│  │          Semantic Core                                     │ │
│  │   Embeddings · Vectorization · RAG · Corporate APIs        │ │
│  └────────────────────────┬───────────────────────────────────┘ │
│                           │                                     │
│  ┌────────────────────────▼───────────────────────────────────┐ │
│  │          Persistence + Observability Layer                 │ │
│  │   PostgreSQL/pgvector · Redis · Tracing · Metrics          │ │
│  └────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
```

---

## Agent Architecture

Each agent follows a consistent pattern:

```
Query
  │
  ▼
┌─────────────────────┐
│  1. Cache Check     │  → Redis short-term memory
└──────────┬──────────┘
           │ miss
           ▼
┌─────────────────────┐
│  2. Retrieval       │  → pgvector semantic search
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  3. Tool Execution  │  → Domain-specific tools
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  4. Reasoning       │  → LLM generation (cached prompt)
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  5. Memory Write    │  → Store result + embeddings
└─────────────────────┘
```

> **Principle**: Reasoning is the last resort, not the first step.  
> Cache → Retrieval → Tools → APIs → Reasoning.

---

## Multi-Agent Orchestration

```
              ┌────────────┐
              │  Planner   │
              │  Agent     │  → decomposes task → generates DAG
              └─────┬──────┘
                    │
         ┌──────────▼──────────┐
         │   Orchestrator      │
         │   Agent             │  → coordinates execution
         │                     │  → manages retries
         └──┬─────────────┬────┘  → aggregates outputs
            │             │
     ┌──────▼──┐     ┌────▼──────┐
     │ Agent A │     │  Agent B  │   ... parallel execution
     └──────┬──┘     └────┬──────┘
            │             │
         ┌──▼─────────────▼──┐
         │   Evaluator Agent │  → reflection loop
         │                   │  → quality validation
         └───────────────────┘
```

---

## Memory Architecture

| Layer | Technology | Purpose | TTL |
|---|---|---|---|
| **Short-term** | Redis | Session context, recent results | 4h |
| **Long-term** | PostgreSQL + pgvector | Semantic memory, embeddings | Permanent |
| **Cognitive** | pgvector (dedicated) | Human RAG chunks | Permanent |

---

## Observability

Every agent exposes:

```
AgentMetrics {
  tokenUsage:      { input: number, output: number, cached: number }
  latencyMs:       number
  costUsd:         number
  retrievalHits:   number
  toolCalls:       ToolCallRecord[]
  workflowTrace:   SpanRecord[]
}
```

---

## Cost Optimization Strategy

| Model | Use Case |
|---|---|
| **Haiku** | Lightweight classification, routing, simple retrieval |
| **Sonnet** | Orchestration, coding, structured generation |
| **Opus** | Planning, reflection, complex reasoning |

Prompt caching is applied on all system prompts via `cache_control: ephemeral`.

---

## Design Principles

1. **Tool-first** — cache → retrieval → tools → reasoning
2. **Memory-aware** — always retrieve before reasoning
3. **Observable** — every agent call is traced and metered
4. **Modular** — enable/disable modules per organization
5. **Cost-conscious** — right model for right task

---

> This document describes conceptual architecture only.  
> No implementation code or proprietary details are included.
