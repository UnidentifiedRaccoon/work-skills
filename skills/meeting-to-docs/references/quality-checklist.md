# Quality Checklist

Use this checklist after both artifacts exist. Fix detected issues before delivery.

## Source coverage

- The primary recording, captions, or existing transcript was actually inspected.
- Every supporting source is marked as inspected, unavailable, or intentionally unused.
- The output does not imply access to a source that could not be opened.
- Conflicts between sources are visible and attributed.

## Transcript

- The first and last substantive moments of the recording are covered.
- Timestamp order is monotonic and the notation is consistent.
- Long gaps are explained by silence, missing media, or an explicit source boundary.
- Every turn has a stable speaker name or label.
- Technical names, identifiers, and URLs match inspected sources.
- Inaudible, overlapping, and uncertain speech is marked rather than guessed.
- Decisions, disagreements, corrections, and commitments have not been cleaned away.

## Participant identity

- Confirmed names have direct or corroborated evidence.
- Probable names are visibly qualified.
- Unresolved voices retain stable labels in both files.
- The final clarification question includes timestamp samples that let the user map each unresolved label.
- No biometric identification or unsupported inference was used.

## Summary

- A new developer can identify the purpose, central flow, normal workflow, and verification point.
- Current behavior, proposals, assumptions, and decisions are not conflated.
- Consequential claims and action items link back to timestamps or named supporting sources.
- Owners and deadlines are stated only when supported.
- Links are exact and described by purpose.
- Mutable facts are dated or qualified.
- Limitations, risks, open questions, and technical debt are not presented as resolved.
- The summary adds structure and explanation instead of merely shortening the transcript.

## Cross-file consistency

- Participant names and labels match exactly.
- Topic, date, duration, and source names do not conflict.
- Summary timestamps exist within the transcript timeline.
- Every decision and action item in `summary.md` is supported by `transcription.md` or a named source.
- After participant clarification, names, roles, ownership, and references are updated in both files.
