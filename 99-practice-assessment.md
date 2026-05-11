# Practice Assessment

> Self-graded mini-exam. 12 questions across 4 domains.

## Instructions

- Time yourself: 18 minutes.
- No looking at the guide.
- Score: 9+ correct = ready. 6-8 = review. <6 = study more.

## Questions

**1.** Which Claude tier should you pick for the highest-throughput, lowest-cost chat workload?
A) Opus B) Sonnet C) Haiku D) Vertex

**2.** Where does a Claude system prompt go in the Messages API?
A) The first user message
B) A top-level `system` field
C) An assistant message
D) Inside a `<system>` tag

**3.** RTCEF stands for...
A) Role, Task, Context, Examples, Format
B) Role, Tools, Context, Eval, Format
C) Reason, Test, Compose, Eval, Finalize
D) Retrieve, Tag, Cache, Embed, Format

**4.** A `stop_reason` of `tool_use` means...
A) The model errored
B) Generation hit max_tokens
C) The model is requesting a tool call
D) The model refused

**5.** Best place to put long source documents in a Claude prompt?
A) End of the prompt
B) Inside the system prompt only
C) Top of the user message, with instructions repeated at the end
D) In a separate API call

**6.** Best defense against prompt injection from RAG content?
A) Higher temperature
B) Wrap untrusted content in tags and instruct Claude to ignore instructions inside
C) Use Opus instead
D) Disable streaming

**7.** Best pattern for a fresh-knowledge Q and A bot over private PDFs?
A) Fine-tune Claude
B) RAG with vector store + reranker + citations
C) Long-running agent
D) Raw API only

**8.** What is MCP?
A) A model checkpoint format
B) Anthropic's billing API
C) An open spec for portable LLM tool servers
D) A vector store

**9.** Which feature gives ~50% discount with a 24-hour SLA?
A) Prompt caching
B) Streaming
C) Message Batches API
D) Extended thinking

**10.** For stable long system prompts repeated millions of times, you should...
A) Inline the prompt
B) Use prompt caching with `cache_control`
C) Move to Opus
D) Disable system prompts

**11.** In production, which is the safest model identifier strategy?
A) Latest alias
B) Pinned dated snapshot per environment
C) Random tier per request
D) Pick based on time of day

**12.** Calibrate LLM-as-judge against...
A) Other LLM judges only
B) A human-labeled held-out set
C) The model card
D) The Trust Center

## Answer key

1-C, 2-B, 3-A, 4-C, 5-C, 6-B, 7-B, 8-C, 9-C, 10-B, 11-B, 12-B.
