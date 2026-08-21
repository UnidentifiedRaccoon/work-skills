# Summary Format

The summary is durable technical documentation, not a shorter transcript. Organize it around how the subject works and how another developer should act.

````markdown
# <How the system or process works>

**Source:** meeting on <date>; <participants or speaker labels>  
**Purpose:** <what a future developer should be able to understand or do>

> Snapshot of the system as discussed on <date>. Mutable details may have changed.

## In short

<One or two paragraphs with the central model and outcome.>

```text
<small system or process flow when useful>
```

## Useful links and materials

- [Label](exact URL) — why it matters

## 1. <First logical stage or concept>

<Current behavior, rationale, dependencies, and evidence such as [03:20–04:10].>

## <Developer workflow>

1. <Step with prerequisites>
2. <Step with observable result>
3. <Verification or fallback>

## Decisions

| Decision | Rationale | Status | Evidence |
|---|---|---|---|
| <decision> | <why> | Confirmed / Proposed | [12:10–13:02] |

## Action items

| Owner | Action | Deadline or status | Evidence |
|---|---|---|---|
| <name or Speaker 2> | <action> | <stated status> | [18:40–19:05] |

## Open questions

- <question and why it matters> — [timestamp]

## Limitations and technical debt

| Limitation | Consequence | Desired direction |
|---|---|---|
| <current constraint> | <impact> | <proposal, if discussed> |

## Terms

| Term | Meaning in this discussion |
|---|---|
| <term> | <meaning> |

## Source coverage and confidence

- Inspected: <sources>
- Unavailable: <sources and access problem>
- Uncertain: <claims or participant mappings that still need confirmation>
````

## Composition rules

- Keep the causal chain explicit: why the problem exists, what happens, where data or control moves, how a developer interacts with it, and how success is checked.
- Put the happy path before edge cases. Separate operational instructions from architecture when both are substantial.
- Use the meeting for intent and decisions; use supporting documents for exact names and factual detail. Name the supporting source when it contributes information not spoken in the meeting.
- Attach timestamps to consequential facts, decisions, action items, contested claims, and ambiguous points. Several related sentences may share one timestamp span.
- Attribute opinions and proposals. “Alex proposed X” is different from “the system does X.”
- Never manufacture an owner, deadline, decision, command, or URL. Use `Not assigned`, `Not stated`, `Proposed`, or `Unresolved`.
- Avoid dumping every transcript detail. Retain information another developer needs to understand the system, reproduce a workflow, avoid a known trap, or continue the work.
- Keep mutable facts dated. Schedules, ownership, UI behavior, performance figures, and supported formats should be framed as “at the time of the meeting” unless verified against a current source.
- If no useful items exist for a section, omit the section rather than leaving an empty template.
