# Learning-path Summaries

> One-paragraph digest per Anthropic learning module.

## Build with Claude

Covers the Messages API, system prompts, message structure, stop reasons, streaming, vision, and counting tokens. The "Get started" path teaches the minimum-viable Claude call in Python or TypeScript and the differences between Anthropic direct, Bedrock, and Vertex.

## Prompt engineering

A library of techniques: be clear and direct, use XML tags, give Claude room to think, use examples, chain prompts, prefill the assistant turn, and avoid the most common anti-patterns. Includes a prompt generator and prompt improver in the Console.

## Tool use

Walks through defining tools with JSON schema, parsing `tool_use` blocks, sending `tool_result`, and shaping `tool_choice`. Includes streaming considerations and parallel tool calls.

## Agents

Anthropic's "Building effective agents" essay distinguishes augmented LLMs, workflows (prompt chaining, routing, parallelization, orchestrator-workers, evaluator-optimizer), and full agents. Strong bias toward the simplest pattern that works.

## Model Context Protocol

Open spec for connecting LLM apps to tools, data, and prompts. Servers advertise capabilities; clients (Claude Desktop, IDEs, custom apps) discover and call them. Standardizes what was previously bespoke per integration.

## Evaluation

Defines golden sets, rubric grading, and LLM-as-judge. Recommends pinning to a dated model snapshot and running regression evals before each upgrade.

## Safety and policy

The Responsible Scaling Policy ties capability levels to required safeguards. The Acceptable Use Policy lists prohibited categories. Customers are accountable for downstream use of Claude in their products.

## Pricing and ops

Prompt caching gives big discounts on stable prefixes. The Batches API gives a ~50% discount with a 24-hour SLA. Track token usage by feature and tenant from day one.
