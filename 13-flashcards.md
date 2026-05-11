# Flashcards

> Click a card to flip. Viewer.html owns CSS and click-to-flip.

<section class="fc-section" data-fc-title="Foundations">
<div class="flashcard-grid">
<div class="flashcard"><div class="fc-q">Three current Claude tiers?</div><div class="fc-a">Haiku (fast/cheap), Sonnet (balanced default), Opus (frontier reasoning).</div></div>
<div class="flashcard"><div class="fc-q">What does stop_reason "tool_use" mean?</div><div class="fc-a">Claude is requesting a tool call; the app must execute the tool and return a tool_result turn.</div></div>
<div class="flashcard"><div class="fc-q">Where does the system prompt live?</div><div class="fc-a">In the top-level "system" field of the Messages API, not inside messages[].</div></div>
<div class="flashcard"><div class="fc-q">Approx tokens per English word?</div><div class="fc-a">About 1.3 tokens per word; 4 chars per token rule of thumb.</div></div>
</div>
</section>

<section class="fc-section" data-fc-title="Prompting">
<div class="flashcard-grid">
<div class="flashcard"><div class="fc-q">RTCEF stands for?</div><div class="fc-a">Role, Task, Context, Examples, Format.</div></div>
<div class="flashcard"><div class="fc-q">Where do you put long documents in the prompt?</div><div class="fc-a">Near the top, with instructions repeated at the end.</div></div>
<div class="flashcard"><div class="fc-q">When to use extended thinking?</div><div class="fc-a">For complex multi-step reasoning where quality matters more than latency.</div></div>
<div class="flashcard"><div class="fc-q">Two defenses against prompt injection?</div><div class="fc-a">Wrap untrusted content in tags + instruct Claude to ignore instructions inside.</div></div>
</div>
</section>

<section class="fc-section" data-fc-title="Architecture">
<div class="flashcard-grid">
<div class="flashcard"><div class="fc-q">RAG vs. fine-tuning?</div><div class="fc-a">RAG for fresh / proprietary knowledge; fine-tuning for stable style or skill changes (rarely needed).</div></div>
<div class="flashcard"><div class="fc-q">What is MCP?</div><div class="fc-a">Model Context Protocol - open spec for portable LLM tool servers.</div></div>
<div class="flashcard"><div class="fc-q">When orchestrator-workers?</div><div class="fc-a">Large input that can be split into independent sub-tasks then synthesized.</div></div>
<div class="flashcard"><div class="fc-q">Why a reranker after vector search?</div><div class="fc-a">Improves top-k relevance using a cross-encoder before LLM consumption.</div></div>
</div>
</section>

<section class="fc-section" data-fc-title="Production">
<div class="flashcard-grid">
<div class="flashcard"><div class="fc-q">Best discount for repeated long system prompts?</div><div class="fc-a">Prompt caching with cache_control on the stable prefix.</div></div>
<div class="flashcard"><div class="fc-q">Best discount for async bulk?</div><div class="fc-a">Message Batches API - ~50% off with 24h SLA.</div></div>
<div class="flashcard"><div class="fc-q">Should production use a "latest" model alias?</div><div class="fc-a">No. Pin to a dated snapshot and upgrade after evals pass.</div></div>
<div class="flashcard"><div class="fc-q">What is LLM-as-judge?</div><div class="fc-a">Using a strong LLM with a rubric to grade other LLM outputs; calibrate against humans.</div></div>
</div>
</section>
