---
name: minimax-h3-prompting
description: Create, audit, rewrite, and troubleshoot production-ready MiniMax H3 local video prompts for T2VA/T2V, I2VA/I2V, FL2VA, L2VA, and R2V/full-reference workflows in ComfyUI. Use when the user asks for H3 prompts, shot timelines, camera motion, synchronized dialogue/audio, image-to-video instructions, first/last-frame interpolation, character replacement, reference-video editing, or prompt conversion from Portuguese or another language.
---

# MiniMax H3 Prompting

Turn a user's idea, script, image, video, or audio references into a prompt that matches the local MiniMax H3 ComfyUI workflow.

## Operating rules

1. Identify the mode before writing: `T2VA`, `I2VA`, `FL2VA`, `L2VA`, or `R2V`.
2. Ask only for missing information that changes the result: duration, aspect ratio, reference roles, required dialogue, and whether audio is generated, copied, or merely referenced.
3. Keep the user's intent, named entities, dialogue, lyrics, and visible text. Never invent dialogue or translate quoted speech unless requested.
4. Write the model-facing prompt in English by default. Preserve user-provided dialogue, lyrics, and visible text in their original language inside the required markers.
5. Build a chronological timeline. Use `[Shot 1]` without a timestamp; later shots use strictly increasing cut times such as `[Shot 2] At 00:03.500, ...`.
6. Describe camera movement naturally with motion type, amplitude, and speed when useful. Do not dump camera keywords at the end of a paragraph.
7. Separate audio layers: dialogue and synchronized diegetic events in the shot description, ambience and physical sounds in `overall_soundscape`, and audience-only score in `non_diegetic_music`.
8. For R2V, define every used reference once and reuse stable labels. Do not confuse an asset label (`<Video 1>`) with the content extracted from it (`<Subject 1>`).
9. Do not promise exact identity, lip-sync, temporal consistency, or text accuracy. State likely failure points and offer a shorter/simpler fallback when the request is overloaded.
10. Return the final prompt in a copy-ready code block, followed by compact settings and one or two targeted notes.

## Mode selection

- **T2VA/T2V**: no visual reference; construct the complete audiovisual timeline.
- **I2VA/I2V**: one starting image; anchor the first frame, preserve its composition, then describe forward motion.
- **FL2VA**: first and last images; describe the continuous path between them, normally as one shot.
- **L2VA**: one ending image; infer a plausible beginning and converge onto the final frame.
- **R2V/full-reference**: references can drive identity, style, motion, camera, scene, voice, audio, or editing structure. Use the six-section reference format.

## Required output contracts

For base modes, output:

```text
[mode-specific alignment instruction, only when required]

integrated_multimodal_description: ...

overall_soundscape: ...

non_diegetic_music: ...
```

For R2V, output these sections in order:

```text
subject_definitions:
summary:
retention_analysis:
detailed_description:
overall_soundscape:
non_diegetic_music:
```

Read the relevant reference before drafting:

- Base modes: `references/base-prompting.md`
- R2V: `references/r2v-full-reference.md`
- Templates and checks: `references/templates-and-checklists.md`
- ComfyUI/local workflow advice: `references/comfyui-local.md`

## Quality pass

Before returning a prompt, verify:

- the mode and reference count match the requested workflow;
- the first/last frame instruction, duration, and cut times agree;
- each shot adds visible or audible information;
- camera, subject position, action, state changes, and transitions are explicit;
- speaker IDs remain stable and every dialogue block has a language tag;
- audio is not duplicated across the three audio sections;
- R2V labels and retention markers are consistent;
- the prompt does not add unwanted cuts, characters, props, or music;
- the prompt remains feasible for the user's duration and reference load.

Use the official sources linked in the reference files for changes to syntax or model behavior.
