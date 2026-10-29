---
name: meeting-to-docs
description: >-
  Create two Markdown artifacts from a recorded technical meeting and its supporting files, diagrams, links, or documents: a timestamped speaker-attributed transcript and a developer-oriented structured summary. Use for meeting transcription, speaker diarization, knowledge transfer, handover documentation, or turning a technical discussion into reusable documentation; do not use for summary-only note taking when there is no recording, captions, or existing transcript to support a transcription.
---

# Meeting To Docs

Turn a meeting and its surrounding materials into two traceable artifacts:

- `transcription.md`: a chronological transcript with timestamps and stable speaker attribution.
- `summary.md`: a focused technical explanation of the core discussion, without meeting timestamps, supported by explanatory diagrams and relevant video frames when available.

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

First identify the central question, problem, or decision. Organize the summary around that subject and its causal logic. When the meeting compares concepts, explain each concept, compare them on shared criteria, and show the tradeoffs and unresolved choice. Do not turn the summary into a chronological meeting report.

Retain the workflows, dependencies, examples, constraints, decisions, and next steps that help a developer understand the central subject. Keep unrelated projects, side conversations, scheduling, and incidental implementation details in the transcript. A secondary topic belongs in the summary only when it explains a consequence or constraint of the main discussion. This selection does not shorten the transcript: it still covers the whole recording.

The default summary has **no meeting timecodes** in prose, tables, captions, or citation links. Link to `transcription.md` once for the full record; keep precise timestamp associations in the private working inventory for verification. The meeting date is useful context and may remain. If the user explicitly requests timestamp citations in the summary, include them.

Build the visual explanation as part of the summary:

- Use diagrams to explain concepts, relationships, workflows, boundaries, or conflicts that are harder to follow in prose. Keep them tied to the discussion; label proposals and illustrative scenarios accurately.
- When video is available, inspect the relevant parts and extract readable frames of the interfaces, diagrams, or demonstrations that help explain the core subject. Prefer a meaningful crop over an unreadable full desktop, and preserve enough context to avoid changing the meaning.
- Place each visual next to the explanation it supports, with a short caption saying what to notice. Use actual source frames for evidence, not generated reconstructions. Do not force decorative diagrams or irrelevant frames; audio-only inputs do not require video assets.
- Save media beside the documents in `assets/`, embed it using paths supported by the host, and verify that the rendered result is legible and the links work. Detailed selection and provenance rules are in `references/summary-format.md`.

Distinguish current behavior, proposals, assumptions, and confirmed decisions. Verify consequential claims against the transcript or named supporting material without adding timecodes back to the summary. Keep source notes brief; detailed coverage and speaker uncertainty belong in the transcript unless they materially affect a summary claim. Do not force a participant roster, glossary, or action table that distracts from the core explanation.

### 5. Finish the text with `humanizer-ru`

After the content and visuals are complete, invoke the locally installed [humanizer-ru](https://github.com/smixs/humanizer-ru) skill before final verification and delivery. This is the default final editing pass for Russian prose, not an optional suggestion when the skill is available.

Resolve `humanizer-ru` through the host's skill catalog and read its actual `SKILL.md`. If it is not listed, check the host's configured local skill directories before concluding it is missing; do not assume one installation path. Follow the installed skill's audit, targeted editing, and verification workflow, including its supporting references and linter. Resolve its resources relative to its own directory. Running only the linter does not replace the editing pass.

Apply it to the Russian prose in `summary.md`, including headings, captions, and explanatory diagram labels, and to agent-written introductions and notes in `transcription.md`. Treat recorded speaker turns and direct quotations as source evidence: do not stylistically rewrite them, even in a readable transcript. Preserve facts, numbers, names, uncertainty, proposal/decision status, technical identifiers, exact UI labels, URLs, asset paths, code, and diagram syntax. Do not add personal opinions, emotions, or invented details to give the text a voice. Keep timestamps in the transcript and out of the summary by default. For non-Russian passages, preserve the requested language and report that this Russian-language editing pass does not apply.

Save the clean edited prose back into the artifacts. Keep the editing audit and lint output in the working inventory, not appended to the documents. If a protected quotation or technical fragment triggers a style rule, preserve it and record the exception; factual fidelity takes priority over a clean style score. Then rerun the meeting checks below, including visual readability if labels changed. State only the editing and checks actually performed.

If `humanizer-ru` is not installed, finish and save the meeting artifacts, disclose that the final editing pass has not run, and offer to install it from the linked repository. Do not install it automatically or substitute a different skill. For example: “`humanizer-ru` не установлен. Установить его из https://github.com/smixs/humanizer-ru и затем отредактировать готовые документы?” If the user accepts, use the host's skill installer, load the installed skill, edit the saved artifacts, and rerun verification. If installation is declined, leave the saved documents available and the skipped pass explicit. If the skill exists but cannot be read or run, report that actual limitation rather than calling it uninstalled or claiming success.

### 6. Verify the pair

Run the checks in [references/quality-checklist.md](references/quality-checklist.md). In particular, verify that:

- the transcript timeline has no unexplained gaps;
- any speaker names or labels used in the summary match the transcript;
- the summary stays on its central subject, has no meeting timecodes by default, and preserves the status of proposals and decisions;
- every consequential claim or action item in the summary is supported by the transcript or a named supporting source;
- diagrams and selected video frames explain the subject, have accurate captions, and render legibly;
- links and identifiers are copied exactly;
- uncertain content remains marked as uncertain;
- the `humanizer-ru` pass was completed on eligible prose, or its missing/unavailable/not-applicable status is explicit; editing preserved the source evidence and document structure;
- neither file claims that an unavailable source was inspected.

### 7. Deliver and, if needed, reconcile identities

Write the files to the user-specified directory. Otherwise use the current task workspace. Default to `transcription.md` and `summary.md`; if either name already exists and the user did not ask to update it, add the meeting date or a short topic slug instead of overwriting it. Keep referenced visual assets with the delivered files, not only in a temporary processing folder.

In the final response, report:

- both file paths;
- which primary and supporting sources were used or unavailable;
- whether participant identities are confirmed, probable, or unresolved;
- important transcription limitations;
- whether the `humanizer-ru` final edit ran; if it is missing, include the installation offer.

When identities remain unresolved, end with one compact question containing the current labels, timestamp samples, and the exact information needed, for example: “Who are Speaker 1 and Speaker 2, and what are their roles?” After the user replies, update participant lists, speaker labels, ownership, and action items wherever they occur in the two files. Apply the final editing pass to any newly written eligible prose, then rerun the identity and consistency checks.
