# Architecture Center

> Pattern catalogue, indexed by problem.

## I need to...

| Problem | Pattern | See |
|---|---|---|
| Answer from my private docs | RAG with citations | 09-arch-ccaf - A |
| Take actions in another system | Tool-using agent | 09-arch-ccaf - B |
| Process a huge document | Orchestrator-workers | 09-arch-ccaf - C |
| Deploy in AWS with VPC isolation | Bedrock private endpoints | 09-arch-ccaf - D |
| Triage incoming requests | Router workflow | This page |
| Improve answer quality iteratively | Evaluator-optimizer | This page |

## Router workflow

```mermaid
flowchart TD
    In["User input"] --> Router["Claude Haiku classifier"]
    Router -->|"billing"| B["Billing specialist prompt"]
    Router -->|"support"| S["Support specialist prompt"]
    Router -->|"sales"| Sa["Sales specialist prompt"]
    B --> Out["Response"]
    S --> Out
    Sa --> Out
```

Use case: customer support inbox, multi-domain chatbots.

## Evaluator-optimizer

```mermaid
flowchart LR
    Gen["Generator (Sonnet)"] --> Out["Draft"]
    Out --> Eval["Evaluator (Sonnet) - score + critique"]
    Eval -->|"pass"| Final["Return"]
    Eval -->|"fail"| Gen
```

Use case: code generation, copywriting, structured extraction.

## Multi-model strategy

```mermaid
flowchart TD
    Req["Request"] --> Cls["Cheap classifier (Haiku)"]
    Cls -->|"simple"| H["Haiku answers"]
    Cls -->|"medium"| So["Sonnet answers"]
    Cls -->|"hard"| Op["Opus answers"]
```

Use case: cost-control routing while keeping quality on hard tasks.
