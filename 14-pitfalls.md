# Pitfalls

> Common mistakes and how to dodge them.

## 1. Treating context window as memory

The model has no memory between calls. Persist state in your app and rehydrate.

## 2. Ignoring stop_reason

`tool_use` is not a failure - it is an instruction to your code. Always branch on `stop_reason`.

## 3. Few-shot examples that contradict the task

Examples teach format and behavior. Inconsistent examples poison output.

## 4. Letting RAG content carry instructions

Wrap retrieved snippets in `<document>` tags and tell Claude to treat them as data.

## 5. Recursive agent loops with no max iterations

Always cap iterations and add timeouts. Log every tool call.

## 6. Using "latest" model aliases in production

Silent upgrades change behavior. Pin to a dated snapshot.

## 7. No PII redaction in logs

Logs are a regulatory liability. Redact at write time, not at search time.

## 8. Tuning temperature to "fix" non-determinism

Use schema validation, output contracts, and stop sequences instead.

## 9. Forgetting prompt caching

If the same 8K-token system prompt runs millions of times, caching is mandatory.

## 10. Doing real-time when batch would do

Non-interactive workloads on the Batches API can halve the bill.

## 11. Trusting LLM-as-judge blindly

Calibrate the judge against human labels on a held-out set before using it as a gate.

## 12. Ignoring the AUP / RSP

Customers are accountable downstream. Build content classifiers and an abuse review queue.
