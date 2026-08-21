---
name: meeting-to-docs
description: >-
  Create two Markdown artifacts from a recorded technical meeting and its supporting files, diagrams, links, or documents: a timestamped speaker-attributed transcript and a developer-oriented structured summary. Use for meeting transcription, speaker diarization, knowledge transfer, handover documentation, or turning a technical discussion into reusable documentation; do not use for summary-only note taking when there is no recording, captions, or existing transcript to support a transcription.
---

# Meeting To Docs

Turn a meeting and its surrounding materials into two traceable artifacts:

- `transcription.md`: a chronological transcript with timestamps and stable speaker attribution.
- `summary.md`: a coherent technical explanation that another developer can use without hearing the recording.

Use names supplied by the user when available. Otherwise infer speaker identities from evidence, but never guess a name merely from a voice.

## Inputs

Treat all user-provided items as one evidence set:

- audio or video recordings;
- captions or an existing rough transcript;
- files, screenshots, diagrams, whiteboards, tables, and code;
- links to services, tickets, dashboards, repositories, or documentation;
- written context about the meeting, its purpose, and likely participants.

The recording, captions, or existing transcript is the primary source for what was said. Supporting material supplies exact spellings, identifiers, diagrams, and background. If two sources disagree, preserve the disagreement instead of silently choosing one.

Write the transcript in the language actually spoken unless the user requests a translation. Write the summary in the user's requested language; when none is specified, use the language of the request or the meeting's dominant language.

This is an instruction-only skill; it does not bundle a speech-to-text engine. The host must be able to inspect the recording directly or provide captions, an existing transcript, or a transcription-capable tool. If no primary source can be read, report that blocker instead of fabricating a transcript.

Do not infer the content of a link from its URL or title. Open it with an authorized connector, browser, or other available tool; if access fails, list it as unavailable. Keep private recordings and documents within authorized surfaces and never make them public merely to process them.

## Work Without an Early Roster Question

Start from the material already provided. Do not ask for the participant list before processing unless the primary recording itself is unavailable or unreadable.

Create both draft files even when some identities remain unresolved. Use stable labels such as `Speaker 1`, `Speaker 2`, and `Speaker 3`; never alternate labels for the same voice. At the end, ask one grouped clarification question only for unresolved identities, then update both files after the user answers.

## Workflow

### 1. Inventory and inspect the sources

Build a private working inventory with:

- source name or URL;
- source type;
- whether it was successfully read;
- its role: primary recording, existing transcript, participant evidence, or technical context;
- notable gaps, conflicts, or access failures.

Preserve the original inputs. If there are several recordings, establish their chronological order and whether timestamps restart in each file. Prefer one continuous meeting timeline; when that is impossible, label the recording part explicitly.

### 2. Produce the transcript

Use the best available transcription-capable tool or native media understanding. Prefer embedded captions or a supplied transcript as a starting point, but verify technical terms, timestamps, and speaker changes against the recording when possible.

For transcription structure and notation, read [references/transcription-format.md](references/transcription-format.md).

Important invariants:

- cover the recording from the first substantive speech through the end;
- attribute every passage to a stable speaker label;
- timestamp every speaker turn or short group of consecutive turns;
- preserve meaning, disagreements, corrections, decisions, and uncertainty;
- correct punctuation and obvious recognition errors without rewriting the speaker's claims;
- spell technical terms, identifiers, and product names using supporting sources when evidence exists;
- mark inaudible or uncertain fragments instead of inventing them;
- keep exact mentioned links in a dedicated section.

### 3. Resolve participant identities from evidence

Use this evidence order:

1. names and roles explicitly provided by the user;
2. self-introductions or direct naming in the recording;
3. meeting metadata, captions, title cards, screen labels, or a supplied attendee list;
4. contextual statements whose mapping is unambiguous, such as “I own service X” when the supplied context identifies that owner.

Cross-check an inferred name against more than one cue when possible. Do not use external face recognition, voice biometrics, or web searches to identify a person from their appearance or voice.

Record identity confidence internally as confirmed, probable, or unresolved. In the files, present probable identities transparently rather than as fact. If a name is unresolved, retain the speaker label and capture one or two diagnostic timestamp samples for the final clarification question.

### 4. Produce the developer-oriented summary

Read [references/summary-format.md](references/summary-format.md) before drafting.

Reconstruct the discussion into a logical path rather than repeating it chronologically. The summary should explain, where relevant:

- the problem and intended outcome;
- the system or process at a glance;
- components, dependencies, interfaces, and data flow;
- the normal operator or developer workflow;
- identifiers, commands, filters, links, diagrams, and examples actually discussed;
- decisions and their rationale;
- alternatives rejected or deferred;
- action items, owners, and deadlines when stated;
- open questions, risks, limitations, and technical debt;
- terms a new developer needs to understand.

Distinguish current behavior, proposals, assumptions, and confirmed decisions. Cite transcript timestamps for consequential facts, decisions, and unresolved points so a reader can trace the summary back to the meeting.

Do not force irrelevant headings. Prefer a small flow diagram when it makes a multi-step system materially easier to understand.

### 5. Verify the pair

Run the checks in [references/quality-checklist.md](references/quality-checklist.md). In particular, verify that:

- the transcript timeline has no unexplained gaps;
- speaker labels are consistent across both files;
- every decision or action item in the summary is supported by the transcript or a named supporting source;
- links and identifiers are copied exactly;
- uncertain content remains marked as uncertain;
- neither file claims that an unavailable source was inspected.

### 6. Deliver and, if needed, reconcile identities

Write the files to the user-specified directory. Otherwise use the current task workspace. Default to `transcription.md` and `summary.md`; if either name already exists and the user did not ask to update it, add the meeting date or a short topic slug instead of overwriting it.

In the final response, report:

- both file paths;
- which primary and supporting sources were used or unavailable;
- whether participant identities are confirmed, probable, or unresolved;
- important transcription limitations.

When identities remain unresolved, end with one compact question containing the current labels, timestamp samples, and the exact information needed, for example: “Who are Speaker 1 and Speaker 2, and what are their roles?” After the user replies, update participant lists, speaker labels, ownership, and action items in both files, then rerun the identity and consistency checks.
