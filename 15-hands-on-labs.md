# Hands-on Labs

> Run these locally with `pip install anthropic` and `ANTHROPIC_API_KEY` set.

## Lab 1: Hello, Claude

```python
import anthropic
client = anthropic.Anthropic()
msg = client.messages.create(
    model="claude-sonnet-4",
    max_tokens=256,
    system="You are a CCAF study coach. Be concise.",
    messages=[{"role": "user", "content": "What is RTCEF?"}],
)
print(msg.content[0].text)
print(msg.usage)
```

Goal: see `input_tokens` and `output_tokens` and verify `stop_reason == "end_turn"`.

## Lab 2: Stream a long answer

```python
with client.messages.stream(
    model="claude-sonnet-4",
    max_tokens=512,
    messages=[{"role": "user", "content": "Explain RAG in 4 paragraphs."}],
) as stream:
    for text in stream.text_stream:
        print(text, end="", flush=True)
```

Goal: render tokens as they arrive.

## Lab 3: Tool use - a calculator

```python
tools = [{
    "name": "add",
    "description": "Add two numbers.",
    "input_schema": {
        "type": "object",
        "properties": {"a": {"type": "number"}, "b": {"type": "number"}},
        "required": ["a", "b"],
    },
}]

resp = client.messages.create(
    model="claude-sonnet-4",
    max_tokens=512,
    tools=tools,
    messages=[{"role": "user", "content": "What is 17 + 25?"}],
)
print(resp.stop_reason, resp.content)
```

Goal: see `stop_reason == "tool_use"` and inspect the `tool_use` block.

## Lab 4: Tiny RAG with in-memory docs

```python
DOCS = {
    "doc1": "Claude Haiku is the fastest, cheapest current tier.",
    "doc2": "Claude Opus is the highest-quality reasoning tier.",
}
question = "Which Claude tier is cheapest?"
context = "\n".join(f"<document id='{k}'>{v}</document>" for k, v in DOCS.items())
prompt = f"{context}\n\nAnswer using only the documents and cite the id."

msg = client.messages.create(
    model="claude-sonnet-4",
    max_tokens=256,
    messages=[{"role": "user", "content": prompt + "\n\nQuestion: " + question}],
)
print(msg.content[0].text)
```

Goal: verify Claude cites `doc1`.

## Lab 5: Prompt caching

```python
LONG_SYSTEM = "You are a CCAF tutor. " + ("Reference rules: ..." * 500)
msg = client.messages.create(
    model="claude-sonnet-4",
    max_tokens=128,
    system=[
        {"type": "text", "text": LONG_SYSTEM, "cache_control": {"type": "ephemeral"}}
    ],
    messages=[{"role": "user", "content": "List 3 production must-haves."}],
)
print(msg.usage)
```

Goal: see `cache_creation_input_tokens` on first call, `cache_read_input_tokens` on next.

## Lab 6: Batches API

Submit 100 messages via the Batches API, poll until `ended`, inspect results. Confirm the ~50% discount in the Console usage view.
