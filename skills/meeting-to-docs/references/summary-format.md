# Summary Format

Write a focused technical explanation of the meeting's central subject. A reader should understand the problem, the proposed concepts or workflow, the meaningful tradeoffs, and what remains undecided without hearing the recording.

## Choose the scope

State the central question before drafting. Use the user's requested focus when supplied; otherwise infer it from the substantive discussion and conclusions.

Include a detail when it helps explain that question, a decision, a constraint, or a next step. Leave unrelated projects, side conversations, meeting logistics, and incidental examples in the full transcript. Keep secondary topics only when their effect on the central subject is explained. For a comparison, organize around the concepts and common criteria; for a technical walkthrough, follow the system or workflow. Do not force every meeting into a two-concept comparison.

## Default structure

Adapt these sections to the subject; omit any that do not help the explanation.

````markdown
# <Central question, concepts, or workflow>

Based on the meeting on <date>. [Full transcript](transcription.md).

<One or two paragraphs explaining the problem, central distinction or flow,
and the outcome or unresolved choice. Identify proposals as proposals.>

## <How the concepts or workflow fit together>

<Explanatory diagram, embedded in a format the host can render.>

## <First concept or stage>

<How it works, why it is useful, and its limits.>

<Relevant frame or crop from the recording, embedded using a working path.>

*<What to notice in this interface or demonstration; distinguish a mockup
from an implemented feature.>*

## <Another concept or stage, when relevant>

<The same level of explanation, so the alternatives or stages are comparable.>

## <Tradeoffs or shared constraints>

| Criterion | <Concept A> | <Concept B> |
|---|---|---|
| <Meaningful criterion> | <Behavior or tradeoff> | <Behavior or tradeoff> |

<Explain any common technical issue. Add a diagram if it clarifies the
relationship or failure scenario.>

## <Decisions and open questions>

<What was agreed, proposed, deferred, or left unresolved. Include next steps,
owners, and deadlines only when stated and relevant to the central subject.>

<Brief source or uncertainty note only if needed to interpret this summary.>
````

## Timecodes and evidence

- The default summary has no meeting timecodes in paragraphs, headings, tables, image captions, or citation links. If the user explicitly requests timestamp citations, include them.
- Keep the meeting date when useful. Ordinary dates, technical durations, and numbers are not meeting timecodes.
- Link once to the full transcript. Retain timestamp associations for consequential claims and source frames in the private working inventory so they can be verified without cluttering the summary.
- Use the recording for intent and decisions; supporting material may supply exact identifiers or interface details. Name a supporting source when it contributes facts not spoken in the meeting. Do not turn a mockup label into an agreed requirement.
- Keep detailed source coverage, speaker identification, and transcription caveats in `transcription.md`. Bring an uncertainty into the summary when it affects a claim the reader needs to assess.

## Diagrams

- Add a visual explanation where the core discussion involves relationships, alternatives, data flow, a multi-step process, access boundaries, or a failure scenario. The diagram should make one of these easier to understand than prose alone.
- Choose the representation to fit the question: a flow for a workflow, parallel paths for competing concepts, or a sequence/state diagram for timing and conflicts. Use a table for a small comparison that needs no diagram.
- Keep labels concrete and readable. Explain a substantial diagram in nearby prose rather than repeating every box in a second list.
- Show only relationships supported by the recording or inspected material. Label a synthesis as an explanatory diagram and a proposal as a proposal; an arrow must not imply that an unresolved step was agreed or implemented.
- Use Mermaid when the destination renders it reliably. Otherwise export a readable SVG or PNG using available diagram tools; retain an editable source when practical. Inspect the rendered result for clipped labels, overlapping arrows, and text that becomes too small at document width.

## Video frames

When a recording contains relevant interfaces, diagrams, or demonstrations, inspect those parts and include frames that explain the core subject. If the input is audio-only, the video is unreadable, or it shows only irrelevant material, do not invent frames or add speaker portraits as decoration.

- Choose frames for a specific explanatory purpose: contrasting concepts, showing a state transition, locating a control, or illustrating a point discussed. Avoid near-duplicates.
- Extract the actual frame. Crop to the useful area when it improves readability, preserving labels and surrounding context needed to understand it. Do not generatively redraw source evidence. Keep an uncropped frame when the crop omits context a reader may need.
- Place the frame beside the relevant explanation. The caption should say what to notice and whether it is a mockup, prototype, or existing interface. Names inside demo data are not evidence of meeting participants.
- Record the source file, frame time, and crop in the private working inventory. Keep those timecodes out of summary captions by default.
- Use a small number of informative frames, selected by relevance rather than a fixed quota. If a useful frame cannot be extracted or read, mention that limitation briefly when it matters to the explanation.

## Delivery and final edit

- After the content and visuals are ready, apply the `humanizer-ru` final editing step in `SKILL.md` to Russian prose, captions, and explanatory labels. Preserve facts, uncertainty, exact quoted labels, and all links; keep the editing report out of the summary. If the skill is missing, save the artifacts and offer installation from https://github.com/smixs/humanizer-ru instead of silently skipping the pass.
- Store images and exported diagrams under `assets/` next to the Markdown files. Embed them using paths supported by the host, and include the assets in the delivery rather than linking to temporary files. Link to a full frame when useful context was cropped out.
- Check the document as a reader: image size, captions, diagram labels, links, and the connection between prose and visuals. Preserve a clear reading path without requiring the reader to open every original.
- Distinguish current behavior, proposals, assumptions, and confirmed decisions. Never invent an owner, deadline, decision, command, or URL.
- Keep mutable facts dated or qualified as the meeting's view. Do not present them as verified current behavior without checking a current source.
- Remove repeated explanations and sections that do not help the central subject. A roster, glossary, or action table is useful only when it serves this document.
