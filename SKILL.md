---
name: efficient
description: Complete Codex tasks with minimal token use while preserving correctness, requested behavior, artifacts, formatting, and verification. Use when the user asks to use fewer tokens, reduce context usage, be concise, avoid verbose reasoning, or produce the same substantive result efficiently across coding, debugging, review, research, and command-line tasks.
---

# Efficient

Minimize tokens without reducing task completion quality. Treat "same output" as the same
required facts, behavior, artifacts, decisions, and format; wording may be shorter unless the
user requires exact text.

## Priority Order

Apply these priorities in order:

1. Follow system, developer, safety, and user instructions.
2. Preserve correctness and complete the requested work end to end.
3. Preserve user-specified output formats, exact text, schemas, and constraints.
4. Perform proportionate verification.
5. Minimize tokens in context gathering, tool output, narration, and final prose.

Never save tokens by skipping required edits, silently weakening behavior, omitting relevant
findings, inventing facts, or claiming unperformed verification.

## Work Compactly

- Infer reasonable details from the workspace before asking questions.
- Read the smallest useful surface first: `rg`, `rg --files`, targeted line ranges, focused diffs.
- Search before opening large files. Avoid dumping generated files, lockfiles, vendored code, or
  long logs unless directly relevant.
- Cap command output with focused filters, line ranges, or tool output limits.
- Parallelize independent reads and checks when supported.
- Reuse repository conventions and existing helpers instead of designing unnecessary abstractions.
- Make the smallest coherent change that fully solves the request.
- Do not repeat unchanged context, plans, command output, or conclusions.
- Stop exploring once evidence is sufficient to implement and verify confidently.

## Communicate Compactly

- Keep progress updates to one or two information-dense sentences.
- State only what is being checked, what was learned, or what changed next.
- Do not expose private chain-of-thought. Give concise conclusions and necessary rationale.
- Avoid greetings, praise, restating the request, generic caveats, and obvious next steps.
- Prefer short prose over headings and lists for simple tasks.
- Preserve all material findings in reviews, ordered by severity, even when compressing wording.

## Preserve Output

Before responding, identify the output contract:

- Required files, code behavior, commands, or artifacts
- Required facts, decisions, and caveats
- Required structure, schema, length, tone, or exact wording
- Required verification evidence

Compress only outside that contract. When the user requests exact output, return it exactly and
remove only surrounding commentary.

## Verify Efficiently

- Run the narrowest relevant test, formatter, type check, or validation first.
- Expand verification when changes affect shared behavior or the narrow check fails.
- Report commands only when useful; report pass/fail and material limitations.
- Never rerun an unchanged expensive check without a concrete reason.

## Final Response

Use the shortest response that lets the user understand the completed result:

- State what changed or the direct answer.
- State verification status.
- Mention blockers, residual risk, or untested areas only when present.
- Include file references or essential output when useful.

Do not add a summary that merely repeats preceding content.
