---
name: minimax-h3-prompting
description: Use when writing, reviewing, repairing, revising, or migrating prompts for MiniMax H3, H3-Context-IR, T2VA, I2VA, FL2VA, L2VA, Ref2VA, Hailuo H3, multimodal reference-to-video, native audio-video generation, or Seedance-to-H3 conversion; also use for repeated edits, stale instructions, replacement, deletion, retiming, or reference-label, camera, dialogue, soundscape, duration, and 7,000-character validation issues.
---

# MiniMax H3 Prompting

## Core principle

Compile a copy-ready H3 prompt, not a generic creative brief. Keep structural labels and all newly written narrative text in English. Preserve the user's original dialogue, lyrics, and visible text verbatim, including language, characters, punctuation, and supplied timing notation.

Treat an integer duration of 4–15 seconds and a maximum of 7,000 Unicode characters (including spaces and logical line breaks) as hard contracts. Do not invent camera motion, unsupported edit behavior, or asset roles.

## Source priority and current-contract verification

Use the official MiniMax model repository and platform documentation for capability and format claims. Read [references/sources.md](references/sources.md) before making a capability claim, resolving a current-contract question, or contradicting a user-supplied assumption. State uncertainty rather than presenting an unsupported operation as available.

Use the local references and validator for the package's compiled-output contract. The validator is deterministic feedback, not a substitute for a current first-party capability check.

## Mode router

Select one schema before drafting. Do not mix a keyframe mode with reference media.

| Input role | Mode | Required shape |
| --- | --- | --- |
| No supplied keyframe or reference media | T2VA | Base three fields |
| One concrete opening frame | I2VA | Base fields plus first-frame alignment |
| Concrete opening and ending frames | FL2VA | Base fields plus first/last alignment |
| One concrete ending frame | L2VA | Base fields plus last-frame alignment |
| Identity, style, source image/video, or source audio references | Ref2VA (validator `R2VA`) | Six reference sections |

Use Ref2VA only with at least one reference image or video; reference audio alone is invalid. Use the supplied first/last frame as a keyframe, not as a general reference. If the requested result combines conflicting roles, ask exactly one narrow question naming those roles and stop until the user selects precedence. Do not propose alternatives or emit multiple prompts.

## Selective reference loading

Load only the material that applies after choosing the mode:

| Situation | Required reference |
| --- | --- |
| T2VA, I2VA, FL2VA, or L2VA | [references/base-modes.md](references/base-modes.md) |
| Ref2VA | [references/ref2va.md](references/ref2va.md) |
| Camera direction, dialogue, lyrics, visible text, voiceover, ambience, or music | [references/camera-audio.md](references/camera-audio.md) |
| Seedance conversion | [references/migration.md](references/migration.md) |
| Any requested change to an existing H3 prompt, including the first revision | [references/revision-compiler.md](references/revision-compiler.md) |
| Capability, format, or availability claim | [references/sources.md](references/sources.md) |
| Returning a newly written or changed prompt | [references/usage-en.md](references/usage-en.md) and [references/usage-ko.md](references/usage-ko.md) |

Do not load usage guides for a review that returns no new or changed prompt. Load both usage guides together and keep their facts aligned.

## Workflow

1. Extract the requested operation: write, review-only, change an existing H3 prompt, or migrate. Record supplied assets, their intended role, duration, ratio, required beats, exact dialogue/lyrics/visible text, and camera constraints. Keep valid user timing unchanged.
2. For review-only, infer the existing schema and report findings without rewriting. Ask for missing duration, media roles, or target mode when they cannot be determined safely.
3. For any change-producing operation on an existing H3 prompt (including repair, replacement, deletion, movement, retiming, or the first revision), load `revision-compiler.md`, reconstruct current active state, and run its full-recompile pipeline. Never patch prior prose or append a change paragraph.
4. Route the mode from current media roles. For migration, translate source bindings by semantic role before selecting the H3 schema.
5. Load the selected references. Build the schema first, then add only requested or necessary detail. Keep a base-mode prompt separate from a Ref2VA prompt.
6. Compile roles, timeline, audio, and camera language. Keep the prompt within the hard duration and Unicode limit while retaining active user-supplied text verbatim.
7. Validate the finished prompt with the required duration, mode, and media manifest. Rewrite and revalidate until there are no errors. Surface warnings that change actual generation settings.
8. Return the prompt and usage material in the required output order.

## Schema compiler

For T2VA, I2VA, FL2VA, and L2VA, use the three English fields in this exact order:

```text
integrated_multimodal_description:
overall_soundscape:
non_diegetic_music:
```

For I2VA, FL2VA, and L2VA, place the exact applicable alignment instruction from `base-modes.md` first, followed by one blank line. Render the actual final shot number and the integer duration to two decimal places in FL2VA/L2VA alignment. Keep Shot 1 untimestamped; begin every later sequential shot with a strictly increasing `At MM:SS.mmm` cut inside the duration.

Start T2VA directly with `integrated_multimodal_description:`. Apart from the exact keyed-mode alignment line, place no preamble or foreign schema header before the first required field. Emit every required top-level header exactly once with a non-empty body, and begin the integrated description with `[Shot 1]`.

For Ref2VA, use these six English sections in this exact order:

```text
subject_definitions:
summary:
retention_analysis:
detailed_description:
overall_soundscape:
non_diegetic_music:
```

Begin `summary` with applicable, non-duplicated task prefixes. Define every independently tracked reference label exactly once in `subject_definitions`; give each tracked label an appropriate retention marker. A `<Picture N>` or `<Video N>` cited only as the source inside another item's definition needs no standalone definition or retention line. If it is used or analyzed separately later, define and retain it explicitly. Put the playback timeline in `detailed_description`, not in the base-mode `integrated_multimodal_description` field.

Start Ref2VA directly with `subject_definitions:` and no preamble. Emit every required top-level header exactly once with a non-empty body. Inside `detailed_description`, establish the overall style in one or two English sentences before `[Shot 1]`, then describe the shots in playback order. The validator allows this style opening while still requiring Shot 1 and sequential shots; base-mode descriptions continue to start directly with `[Shot 1]`. Give every independently tracked reference label exactly one anchored retention line using only the visual or audio marker family in `ref2va.md`; these markers describe the requested relationship and never guarantee semantic fidelity.

## Reference-role compiler

Before drafting, create one internal record for every supplied asset. Each record must contain:

- Source asset identifier and exact H3 semantic label.
- Primary semantic role and an allowed secondary role when needed.
- Features to preserve and features allowed to change.
- Conflict priority against every competing reference.
- Applicable shots or time ranges.

Resolve conflicts in these records before writing the schema. Assign source assets by semantic role:

- Use `<Subject N>` for reusable identity, appearance, prop, environment, style, action, expression, or pose.
- Use `<Picture N>` for a concrete composition/keyframe anchor.
- Use `<Video N>` only for direct editing, continuation, or whole-video camera/cut/rhythm structure.
- Use `<Audio N>` for copied or referenced voice, music, dialogue, effects, beat, or continuity.

Number `<Video N>` and `<Audio N>` independently. Bind a referenced speaking voice to the target speaker ID when applicable. Do not leave Seedance `@` bindings in H3 output, convert every image into a picture label, or imply that a video supplies an audio label.

For a Seedance image, define a `<Subject N>` when it supplies identity, style, clothing, a prop, an environment, an action, expression, or pose. Reserve `<Picture N>` for a concrete composition, keyframe, or frame-alignment role. Preserve usable roles and intent while warning that direct deletion, object-only replacement, exact extension, and precise between-video filling are regeneration or external-editing work unless a current official source proves otherwise.

When an asset-role map is returned, expose the user-relevant record fields compactly: asset, H3 label, primary role, any secondary role, preserve features, changeable features, conflict priority, and applicable shots/time ranges. Keep identity/style images as `<Subject N>` and concrete composition/keyframes as `<Picture N>`.

## Timeline and camera compiler

Describe visible composition, subjects, setting/light, observable action or state change, sound, and camera in playback order. Use a new shot for a new subject, space, state, viewpoint, or time; use camera movement for a limited distance or angle change.

Write each requested camera action accurately: distinguish zoom from physical push, pan from truck, tilt from pedestal, arc from subject rotation, and rack focus from camera movement. Use one primary move per beat and do not add a default push-in. Preserve explicit user camera direction and beat timing.

Give vocal events stable `(S1)`, `(S2)` IDs in vocal-event order. Put only `[Language]` plus the verbatim supplied dialogue or lyric inside `<d>`. Keep visible text outside `<d>` in English double quotation marks, retaining the supplied text verbatim. Follow `camera-audio.md` for voiceover, cross-cut continuation, cutoff, diegetic sound, ambience, and score separation.

## Language and length contract

Write H3 labels, section headings, alignment instructions, retention analysis, camera directions, and new narrative prose in English. Preserve original dialogue, lyrics, and visible text exactly; do not translate, normalize typography, or replace supplied time ranges.

Count Unicode characters in the prompt block itself. Settings notes, role maps, validator results, `사용 설명`, and `Usage Notes` remain outside that block. Compress newly written prose before changing any user-provided text. Select an integer duration from 4 through 15 seconds; never round or snap a valid supplied duration without the user's instruction.

## Validation loop

Write the prompt block to a temporary UTF-8 file. When any media asset is present, write a temporary UTF-8 JSON manifest with non-negative integer counts for only these keys: `first_frames`, `last_frames`, `reference_images`, `reference_videos`, and `reference_audios`.

Resolve the validator from the installed skill root: set `$skillRoot` to the parent directory of the loaded `SKILL.md`, then use `scripts/validate_h3_prompt.py` beneath it. Select an available Python 3 interpreter (`python3`, `python`, or the Windows `py -3` launcher). Run with the selected `DURATION` and validator mode (`R2VA` for Ref2VA):

```powershell
$skillRoot = Split-Path -Parent (Resolve-Path 'PATH_TO_LOADED_SKILL\SKILL.md')
$validator = Join-Path $skillRoot 'scripts\validate_h3_prompt.py'
$python = Get-Command python3 -ErrorAction SilentlyContinue
if (-not $python) { $python = Get-Command python -ErrorAction SilentlyContinue }
if ($python) {
  & $python.Source $validator PROMPT_PATH --duration DURATION --mode MODE
} elseif (Get-Command py -ErrorAction SilentlyContinue) {
  & py -3 $validator PROMPT_PATH --duration DURATION --mode MODE
} else { throw 'Python 3 is required.' }
```

Optional approved local override/example for this workstation:

```powershell
$pythonExe = 'C:\Users\namhe\.cache\codex-runtimes\codex-primary-runtime\dependencies\python\python.exe'
$skillRoot = 'C:\Users\namhe\.codex\skills\minimax-h3-prompting'
& $pythonExe (Join-Path $skillRoot 'scripts\validate_h3_prompt.py') `
  PROMPT_PATH --duration DURATION --mode MODE
```

Add `--manifest MANIFEST_PATH` when the manifest exists. Read the first summary line and every diagnostic. Rewrite for each error, rerun the same command, and continue until it exits 0 with no errors. Put every material warning that affects generation settings in the optional first-line assumption/settings note. Delete the temporary prompt and manifest after validation.

## Review, repair, and migration routing

For review, identify the detected/claimed mode, schema/order errors, alignment, duration, Unicode count, timeline, labels, retention, dialogue, and media-role errors. Report actionable findings; provide no rewritten prompt unless the user asks for repair.

For repair or any other requested change to an existing H3 prompt, reconstruct Revision State from the latest full prompt and active conversation requirements. Apply the requested operation, invalidate every dependent structure, and compile one complete replacement prompt from current state. Preserve unrelated active intent, exact active dialogue/lyrics/visible text, valid beats, and compatible media roles. Remove deleted or superseded content and anything derived only from it; do not turn it into a caution, silence directive, retry control, alternative, or historical note. Then run the validation loop and return the recompiled prompt.

For Seedance migration, first read `migration.md`; map assets by semantics, remove source-only binding syntax, select a valid H3 mode, and disclose unsupported-operation limits. Validate the resulting H3 prompt as a new prompt.

## Output contract

For a new or changed prompt, emit exactly this order:

1. An optional one-line assumption/settings note containing all material validator warnings when any exist.
2. One English H3 prompt code block and no other code block.
3. `Prompt length: N/7000 characters` using the validator count.
4. A compact asset-role map when references or keyframes exist.
5. `사용 설명` with Korean usage facts.
6. `Usage Notes` with the same facts in English.
7. For repairs only, one narrow retry instruction. For a revision, target only the current change-producing operation and facts that remain active after it; never target an earlier repair. For a pure `REMOVE`, omit this slot when a retry would require negative, silence/no-speech/closed-lips, historical, or deleted-state wording.

Keep the role map and both usage-note sections outside the H3 code block. State matching current mode, asset-role, duration/ratio, active verbatim-text, copy-only, and validation facts in both usage sections. When slot 7 applies, bind it to the current operation only; never substitute an older active repair. Do not add patch prose, a change log, or a retry instruction derived from deleted or superseded state.

## Final checklist

- Select exactly one valid mode and its matching schema.
- Keep all structural and newly written narrative prompt text English.
- Preserve original dialogue, lyrics, visible text, and valid timings verbatim.
- Use integer 4–15-second duration and no more than 7,000 Unicode characters.
- Use exact keyframe alignment and ordered fields/sections.
- Define and retain every Ref2VA label consistently; keep video and audio numbering independent.
- Separate dialogue, ambience, diegetic sound, and non-diegetic music.
- For every change to an existing prompt, fully recompile from current active state and reject stale, deleted, superseded, or orphaned instructions in the prompt, role map, and usage notes.
- If repair slot 7 applies, target only the current operation and active resulting facts; omit it for a pure removal that would require negative or deleted-state wording, and never fall back to an earlier repair.
- Validate with the selected mode and manifest, fix every error, and retain relevant warnings.
- Return one English H3 code block, then count, optional role map, `사용 설명`, and matching `Usage Notes`.
