# Extra CCAF Concepts

> Concepts that often show up but do not own a domain page.

## Constitutional AI (CAI)

A training technique where the model critiques and revises its own answers against a written "constitution" of principles. Reduces dependence on raw human preference data and produces more consistent harm-avoidance.

## RLHF in one minute

1. Train base LLM on text.
2. Train a reward model on human preference pairs.
3. Fine-tune the LLM with RL to maximize the reward model.
4. Iterate with red-teaming.

## Context window math

- Token approx 4 chars of English.
- 200K tokens approx 150K words approx 500 pages.
- Cost scales with tokens in + tokens out. Cached tokens are billed at a discount.

## Streaming events

- `message_start`, `content_block_start`, `content_block_delta`, `content_block_stop`, `message_delta`, `message_stop`.
- Use deltas for typewriter UX, not full message replays.

## Citations and source grounding

- Use `<document>` tags with `<source>` ids; instruct Claude to cite sources by id.
- Validate that cited spans exist in the source text before showing to the user.

## Vision input

- Pass images as `image` content blocks (base64 or URL).
- Charts, screenshots, and document scans are supported; ask for structured extraction.

## Computer use (preview)

- Claude can drive a virtual desktop via screenshots + actions.
- High-risk capability: sandbox, allow-list domains, never run on production hosts.

## Multi-turn memory patterns

- Summarize older turns and feed as `<history_summary>` in system.
- Use external store keyed by conversation id; rehydrate on each call.
