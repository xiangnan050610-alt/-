# Templates and Checklists

## T2VA template

```text
integrated_multimodal_description: [Shot 1] [style], [framing] establishes [subject and setting]. [Action and camera]. [Speaker ID] says: <d>[Language] exact dialogue</d>. [Shot 2] At 00:SS.mmm, [cut or continuous camera move] ...

overall_soundscape: [ambient bed]. [physical sounds]. [non-verbal human sounds].

non_diegetic_music: [instrumentation], [tempo], [rhythmic/dynamic development].
```

## I2VA template

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] [Style and composition from Picture 1] remains consistent. [Action onset]. [Continuous development]. [Result/reaction].

overall_soundscape: ...

non_diegetic_music: ...
```

## FL2VA template

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 08.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] [Opening state from Picture 1]. [Observable continuous changes]. [Final state exactly reaches Picture 2].

overall_soundscape: ...

non_diegetic_music: ...
```

## L2VA template

```text
How the reference pictures align with the target video — <Picture 1> (from [Shot 1]) aligns with the 08.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] [Plausible preceding state]. [Action and transition path]. [Final shot converges on Picture 1].

overall_soundscape: ...

non_diegetic_music: ...
```

## R2V template

```text
subject_definitions:
<Subject 1> is ...
<Video 1> is ...
<Picture 1> is ...
<Audio 1> is ...

summary: [reference generation] ...

retention_analysis:
<Subject 1> (appears in [Shot 1]): fully_preserved - ...
<Video 1> (camera and timing): fully_preserved - ...
<Audio 1>: reference - ...

detailed_description:
The target video is ...
[Shot 1] ...
[Shot 2] At 00:04.000, ...

overall_soundscape: ...

non_diegetic_music: ...
```

## Failure checks

- Avoid vague requests such as `make it cinematic` without subject, action, camera, and timeline details.
- Avoid conflicting camera moves in one shot.
- Avoid adding timestamps to `[Shot 1]`.
- Avoid reusing `(S1)` for a different speaker.
- Avoid placing dialogue in `overall_soundscape`.
- Avoid defining `<Picture 1>` as both a character reference and a final-frame anchor without saying which role applies.
- Avoid introducing a `<Video N>` when the input is only a motion reference and is not being edited or continued.
- Avoid asking for too many cuts, characters, references, actions, and audio events in a short clip.
