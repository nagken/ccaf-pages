# Glossary

| Term | Definition |
|---|---|
| Token | Sub-word unit; Claude bills by input + output tokens. |
| Context window | Maximum tokens the model can consider in one call. |
| System prompt | Persona / global rules sent outside the messages array. |
| Stop reason | Why generation ended: end_turn, max_tokens, stop_sequence, tool_use. |
| RTCEF | Role, Task, Context, Examples, Format - prompt structure. |
| Few-shot | Including labeled examples in the prompt to teach format. |
| Extended thinking | Mode where Claude produces hidden reasoning before answering. |
| RAG | Retrieval-augmented generation - inject retrieved docs into prompt. |
| Embedding | Vector representation of text used for semantic search. |
| Reranker | Second-pass model that re-orders retrieval candidates. |
| Tool use | Mechanism for Claude to request a typed function call. |
| MCP | Model Context Protocol - open spec for LLM tool servers. |
| Agent | LLM loop that plans, calls tools, observes, and iterates. |
| Constitutional AI | Training method using a written set of principles. |
| RLHF | Reinforcement learning from human feedback. |
| RSP | Anthropic Responsible Scaling Policy. |
| AUP | Acceptable Use Policy. |
| Prompt caching | Discounted billing for repeated stable prompt prefixes. |
| Batches API | Async bulk endpoint with ~50% discount and 24h SLA. |
| Jailbreak | Adversarial prompt to bypass safety guardrails. |
| Prompt injection | Hostile instructions hidden in tool / RAG content. |
| Golden set | Curated input-output pairs used for regression eval. |
| LLM-as-judge | Using an LLM to grade another LLM's outputs. |
| Snapshot model | Dated model id; pinning prevents silent upgrades. |
