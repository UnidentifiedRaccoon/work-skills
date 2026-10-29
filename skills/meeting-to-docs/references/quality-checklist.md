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
- Unresolved voices retain stable labels in the transcript and wherever they are referenced in the summary.
- The final clarification question includes timestamp samples that let the user map each unresolved label.
- No biometric identification or unsupported inference was used.

## Summary

- The central question, concepts, or workflow is clear early in the document.
- The reading order follows the subject rather than the chronology of the conversation.
- Unrelated projects, side conversations, and meeting logistics are omitted; any secondary topic explains a constraint or consequence of the main discussion.
- There are no meeting timecodes in summary prose, headings, tables, captions, or citation links unless the user explicitly requested them. A meeting date is allowed.
- A link to the full transcript provides access to the complete record; consequential claims remain traceable through the private working inventory or named supporting sources.
- Current behavior, proposals, assumptions, and decisions are not conflated; an unresolved choice remains unresolved.
- Owners and deadlines are stated only when supported and relevant to the central subject.
- Links and identifiers are exact, and mutable facts are dated or qualified.
- Source and identity caveats are brief and included only when needed to assess a summary claim.
- The summary explains the subject rather than merely shortening the transcript.

## Visuals

- Diagrams clarify the core relationships, concepts, workflow, or conflict where a visual explanation is useful; they do not invent architecture or settled decisions.
- Relevant video demonstrations were inspected and informative frames included when available. Omitted frames have a real reason, such as audio-only input, unreadable video, or no relevant visual content.
- Frames are extracted from the source, with enough context retained to preserve their meaning; demonstration data is not treated as participant evidence.
- Captions explain what to notice and distinguish mockups/proposals from implemented behavior, without meeting timecodes by default.
- Diagram labels, arrows, and screenshot text are readable at the document's display size.
- Each visual is placed near the explanation it supports; decorative and redundant images are omitted.
- Asset files are delivered beside the documents, all embedded paths resolve in the host, and no output depends only on a temporary processing folder.
- Source frame times and crops are recorded in the private working inventory.

## Final editing with `humanizer-ru`

- Local availability was checked through the skill catalog or configured skill directories.
- When available, the actual installed skill and required references were read, and its audit, editing, and verification workflow was applied to eligible Russian prose; a lint-only run does not count as the editing pass.
- The linter ran, or the installed skill's manual fallback was used and reported accurately. Protected quotations or technical fragments were preserved, with any style exceptions recorded.
- Speaker turns, quotations, facts, numbers, names, uncertainty, and proposal/decision status survived the edit unchanged in meaning.
- URLs, asset paths, identifiers, exact UI labels, code, diagram syntax, and the transcript timeline remain intact; summary timecodes were not reintroduced.
- The clean text is saved in the artifacts; editing reports and lint output stay in the working inventory. Changed diagram labels were rendered and checked again.
- If the skill is missing, the artifacts are saved, the skipped pass is disclosed, and installation from https://github.com/smixs/humanizer-ru is offered rather than performed automatically. An unreadable or failed installation is reported as such.
- Non-Russian passages keep their requested language; the Russian-only pass is marked not applicable where needed.

## Cross-file consistency

- Participant names and labels match wherever used in both files; the summary need not repeat the full roster.
- The summary focus is supported by the meeting; dates, durations, and source names match wherever stated.
- The transcript retains its complete timestamped timeline, including substantive side topics omitted from the summary.
- If the user requested summary timestamp citations, those timestamps are within the transcript timeline.
- Every decision and action item in `summary.md` is supported by `transcription.md` or a named source.
- After participant clarification, names, roles, ownership, and references are updated wherever they occur in the two files.
