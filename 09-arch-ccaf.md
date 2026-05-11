# Architectures - CCAF

> Reference architectures for typical Claude workloads.

## A. Chat with your docs (RAG)

```mermaid
flowchart LR
    U["User"] --> App["App backend"]
    App --> Emb["Embed query (Voyage)"]
    Emb --> Vec["Vector store"]
    Vec --> Re["Reranker"]
    Re --> Prompt["Compose prompt with <document> tags"]
    Prompt --> Claude["Claude Messages API"]
    Claude --> App
    App --> U
```

Key choices: chunk size, overlap, embedding model, top-k, reranker, citation enforcement.

## B. Tool-using agent

```mermaid
flowchart TD
    Start["User request"] --> Plan["Claude: plan + tool_use"]
    Plan --> Run["Backend executes tool"]
    Run --> Feed["Append tool_result"]
    Feed --> Loop{"stop_reason == end_turn?"}
    Loop -- No --> Plan
    Loop -- Yes --> Answer["Return final answer"]
```

Guardrails: max iterations, allow-listed tools, audit log, dry-run mode for destructive tools.

## C. Orchestrator-workers for long docs

```mermaid
flowchart TD
    Orch["Orchestrator (Sonnet)"] --> Split["Split into sections"]
    Split --> W1["Worker 1 (Haiku)"]
    Split --> W2["Worker 2 (Haiku)"]
    Split --> W3["Worker N (Haiku)"]
    W1 --> Merge["Merge + final synthesis (Sonnet/Opus)"]
    W2 --> Merge
    W3 --> Merge
```

Pattern: cheap workers fan out, premium model reassembles.

## D. Enterprise deployment on Bedrock

```mermaid
flowchart LR
    Client["VPC client"] --> APIGW["API Gateway / private endpoint"]
    APIGW --> Lambda["Lambda or ECS"]
    Lambda --> Bedrock["Bedrock InvokeModel"]
    Bedrock --> Claude["Claude (Anthropic on AWS)"]
    Lambda --> Logs["CloudWatch + S3 + KMS"]
    Lambda --> Vec["OpenSearch vector"]
```

Controls: IAM least privilege, KMS at rest, VPC endpoints, CloudTrail, Bedrock Guardrails.
