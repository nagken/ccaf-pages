# CCAF Visual Study Guide - Master Index

> Claude Certified Foundation Architect. Concept-only. ASCII content.

```mermaid
mindmap
  root((CCAF))
    Foundations
      Models
        Haiku
        Sonnet
        Opus
      Messages API
        system
        messages
        stop_reason
      Training
        Pretraining
        RLHF
        Constitutional AI
      Policy
        AUP
        RSP
    Prompt Engineering
      RTCEF
        Role
        Task
        Context
        Examples
        Format
      XML tags
      Long context
      Extended thinking
      Injection defense
    Application Design
      RAG
        Embed
        Vector
        Rerank
      Tool use
        Schemas
        Agent loop
      MCP
      Workflows
        Router
        Parallel
        Orchestrator
        Evaluator
      Deployment
        Anthropic
        Bedrock
        Vertex
    Production Ops
      Evaluation
        Golden set
        LLM as judge
      Safety
        Guardrails
        PII
      FinOps
        Prompt caching
        Batches API
      Reliability
        Retry
        Idempotency
        Model pinning
```

## Domain map

```mermaid
flowchart LR
    Exam["CCAF"]
    Exam --> D1["01 Claude Foundations - 25%"]
    Exam --> D2["02 Prompt Engineering - 25%"]
    Exam --> D3["03 Application Design - 25%"]
    Exam --> D4["04 Production Operations - 25%"]
```

## Weighting

```mermaid
pie showData
    title CCAF domain weights
    "Foundations" : 25
    "Prompt Engineering" : 25
    "Application Design" : 25
    "Production Operations" : 25
```

## Study plan (suggested)

| Week | Focus | Pages |
|---|---|---|
| 1 | Foundations + API basics | 01, 05, 07 |
| 2 | Prompt engineering deep dive | 02, 13, 14 |
| 3 | RAG, tools, agents, MCP | 03, 09, 16 |
| 4 | Production, eval, ops, policy | 04, 06, 08, 11 |
| 5 | Hands-on labs + flashcards + quiz | 15, 13, 17 |

## How to use this guide

1. Read each domain page once.
2. Click links in the diagrams - they deep-link to Anthropic docs.
3. Run the labs in `15-hands-on-labs.md`.
4. Drill with `13-flashcards.md`.
5. Self-quiz via `17-copilot-quiz.md`.
