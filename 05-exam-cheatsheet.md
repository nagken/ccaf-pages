# Exam Cheatsheet

> One-pager. ASCII only.

## Model tiers at a glance

| Tier | Use for | Trade-off |
|---|---|---|
| Haiku | High-volume, latency-sensitive | Lowest cost, broadest capability floor. |
| Sonnet | Default production workloads | Best price / performance. |
| Opus | Hardest reasoning, agents | Highest quality, highest cost. |

## Anthropic Messages API skeleton

```python
import anthropic
client = anthropic.Anthropic()
resp = client.messages.create(
    model="claude-sonnet-4",
    max_tokens=1024,
    system="You are a helpful CCAF tutor.",
    messages=[{"role": "user", "content": "Summarize RAG in 3 bullets."}],
)
print(resp.content[0].text, resp.stop_reason)
```

## Stop reasons

- `end_turn` - normal completion.
- `max_tokens` - hit `max_tokens` cap; output may be truncated.
- `stop_sequence` - hit a configured stop string.
- `tool_use` - model is requesting a tool call; respond with `tool_result`.

## Prompt structure (RTCEF)

1. Role - who Claude is acting as.
2. Task - what to do.
3. Context - background data (docs, knowledge).
4. Examples - few-shot demonstrations.
5. Format - exact output contract.

## Tool use loop

1. Send `messages` + `tools` definitions.
2. If `stop_reason == "tool_use"`, parse `tool_use` block, run the tool.
3. Append `assistant` (tool_use) and `user` (tool_result) turns, call again.
4. Repeat until `stop_reason == "end_turn"` or max-iterations guard.

## Production must-haves

- Golden eval set + LLM-as-judge gates.
- Prompt caching on stable prefixes.
- Batches API for async bulk.
- Pinned model snapshot per environment.
- PII redaction in logs.
- Retry with jitter; idempotency keys on writes.

## Common XML tags

- `<context>`, `<document>`, `<example>`, `<thinking>`, `<answer>`, `<user_content>`.
