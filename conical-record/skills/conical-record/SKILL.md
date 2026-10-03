---
name: conical-record
description: Use the user's Conical Forum record, the beliefs they have stated, domains they have explored and how they tend to think. Use when a question is about the user themselves ("what did I think about X", "how do I usually handle Y"), when personalizing advice on a personal decision or plan, or when the user asks to remember something, save a conversation, or tidy their record.
---

# Conical Forum record

The Conical Forum connector exposes the user's own record: beliefs they stated or that were inferred from
their reflections, domains they have explored, and tendencies from their assessments. Use it deliberately, not
on every turn.

## When to use it

- The question is about the user or their history would change your answer. Do not call tools just to look
  thorough, and never guess what is in the record.
- Before advising on a personal decision or plan, call `get_user_context` with a short topic. It is cheap and
  returns current beliefs, stated ones first. Weave the results into plain advice and cite them.
- For a specific question about the user, use `ask_record` (scope it with a domain slug when the question
  clearly belongs to one domain).
- To anticipate how they tend to handle a described situation, use `how_do_i_approach`.
- For recall ("what did I think about X?", "did I change my mind?"), use `what_did_i_think`, which includes
  revisions and retractions. To search broadly use `search`, then `fetch` with the id exactly as returned
  (`belief:<id>`, `conversation:<id>` or `wrapup:<id>`).

## Never

- Do not reveal or invent scores or personality labels. Results describe tendencies in words, so keep them in words.
- Do not guess identifiers. Domain slugs come from `list_domains`, and belief ids come from `what_did_i_think`,
  `search` or `review_queue`. If a tool says a domain was not found, call `list_domains` and retry once.
- Do not present inferred beliefs as things the user said. Say whether each was stated or inferred. Stated beliefs
  outrank inferred ones, and if they conflict, show both and let the user decide.
- Do not save your own inferences about the user as theirs.

## Writing to the record

Writes go to a permanent record, so act only on the user's request, or after offering once and getting a yes.

- `record_belief`: only when the user states a belief or asks you to remember it, in their first-person voice.
- `refine_belief`: when the user reacts to a belief ("that's not true anymore", "yes, that's right"), find it and
  confirm, revise (with `new_claim`) or retract. History is kept. If a belief was already superseded, look up its
  current version instead of retrying.
- `record_entry`: the user's own journal text. `save_conversation`: a transcript of the current chat with clear
  speaker labels, once per conversation. Analysis runs in the background, so results appear shortly, not instantly.
- To tidy the record, use `review_queue` and walk the user through items one at a time, applying their answers
  with `refine_belief`. Never decide for them.

## Feedback

If the user says a result was or was not useful, call `rate_result` with the `invocation_id` returned with that
result.

## Empty or limited results

An empty result means nothing is recorded yet, so say so. Some tools may be missing because the user granted
limited access, so work with what is available.
