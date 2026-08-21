# Transcript Format

Use this structure as a strong default. Omit fields that truly cannot be established, but make uncertainty visible.

```markdown
# Meeting transcript: <topic>

**Date:** <date or unknown>  
**Duration:** <HH:MM:SS>  
**Primary source:** <recording or transcript name>  
**Supporting sources:** <files and links actually inspected>

## Participants

- <Name — role> (confirmed)
- <Probable name — role> (probable; evidence: <short explanation>)
- Speaker 3 (unresolved)

## Transcript

### <Topic or phase>

**[00:00–00:18] Name / Speaker 1:** Speech with lightly normalized punctuation.

**[00:18–00:31] Name / Speaker 2:** Next turn.

**[00:31–00:36] Speaker 1:** [inaudible 00:33–00:35] followed by clear speech.

## Mentioned materials

- [Human-readable label](exact URL)
- `exact-file-name.ext` — how it was discussed

## Unclear fragments

- `[00:33–00:35]` — speech is masked by overlap.
- `[12:08]` — product name sounds like “ExampleX”; spelling is unconfirmed.
```

## Timestamp rules

- Use `[MM:SS–MM:SS]` for meetings shorter than one hour and `[HH:MM:SS–HH:MM:SS]` for longer recordings. Do not mix the two within one file.
- Timestamp each speaker turn. Merge adjacent utterances only when the speaker, topic, and intent are unchanged and the merged span remains easy to locate.
- Start a new topic heading when the conversation changes problem, system component, workflow, decision, or action area.
- For multiple source files, prefer a continuous timeline. If timing cannot be reconciled, prefix each section with `Recording 1`, `Recording 2`, and restart timestamps transparently.

## Fidelity rules

- Default to a readable transcript, not phonetic verbatim: fix punctuation, remove accidental duplicate words, and collapse filler only when meaning and tone are unaffected.
- Preserve hedging, disagreement, corrections, and uncertainty. Do not turn “maybe” into a decision.
- Never silently replace unclear speech with a plausible technical term. Use `[unclear]` or append `(?)` and list the fragment under `Unclear fragments`.
- Mark simultaneous speech as `[overlap]` when it affects interpretation.
- Use supporting files to correct exact spellings, URLs, identifiers, and code tokens, but not to insert statements that were never made.
- If the user requests verbatim transcription, retain filler, false starts, repetitions, and grammatical errors while keeping the same timestamp and uncertainty notation.

## Speaker labels

- Use a confirmed name everywhere once the mapping is supported.
- Use `Probable: <Name>` only when evidence is meaningful but not conclusive.
- Otherwise use stable neutral labels such as `Speaker 1`.
- Roles belong in the participant list; repeat them in turns only when needed to distinguish people with the same name.
