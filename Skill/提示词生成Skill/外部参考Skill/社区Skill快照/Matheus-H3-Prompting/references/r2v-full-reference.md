# MiniMax H3 R2V / Full-Reference Prompting

R2V is stricter than base T2V/I2V. It uses a six-section rewrite format and stable labels for every reference role.

## Six sections

1. `subject_definitions`: define reusable people, objects, environments, styles, actions, voices, images, videos, and audio.
2. `summary`: one short paragraph beginning with a task prefix such as `[reference generation]` or `[video editing + audio reuse]`.
3. `retention_analysis`: one line per reference label explaining what is preserved, transferred, or merely referenced.
4. `detailed_description`: the shot-by-shot playback timeline, normally detailed rather than a plot summary.
5. `overall_soundscape`: ambience and physical sounds across the clip.
6. `non_diegetic_music`: audience-only music, or `N/A`.

## Stable labels

- `<Subject N>`: reusable visible content, such as a person, costume, object, environment, style, pose, or effect.
- `<Picture N>`: a concrete image anchor, storyboard, first frame, keyframe, or last frame.
- `<Video N>`: a source video's temporal/camera/editing structure or continuation source.
- `<Audio N>`: a standalone audio asset, copied soundtrack, voice timbre, music, or sound reference.

Number each category independently. A source video can be `<Video 1>` and its audio can be `<Audio 2>`; the numbers do not imply pairing.

## Reference-role discipline

Assign each reference a job in the prompt: identity, style, environment, motion, camera, composition, voice, music, or editing structure. State the assignment explicitly. For character replacement, preserve the source video's framing, cuts, choreography, camera motion, environment, and timing, then transfer only the requested subject attributes.

Use `<Subject N>` for the content extracted from a file, not as a substitute for the file itself. Use `<Video N>` when the video structure is being edited, continued, or referenced. Use `<Audio N>` only when an audio signal or audio property is actually relevant.

## Summary task prefixes

Use only the relationships that are true:

- `[keyframe completion]`
- `[reference generation]`
- `[video editing]`
- `[video continuation]`
- `[audio reuse]`
- `[audio reference]`

Combine with ` + ` when needed. Do not call an input `video editing` merely because it supplies motion or camera inspiration.

## Retention markers

For visible references use `fully_preserved`, `partially_preserved`, `attribute_transfer`, or `weak_reference`. For audio use `fully_copy`, `partially_copy`, `reference`, or `weak_reference`. Describe the defined role, not every new event introduced by the target prompt.

## Detailed description

Open with one or two sentences defining the target style, then write the chronological shots. Insert labels where their content first appears and where their role matters. Preserve camera and speaker rules from `base-prompting.md`. Do not reduce the section to a relationship list; describe composition, lighting, positions, state changes, actions, camera, sound, and the exact reference effect.

## Character-swap pattern

For a strict identity replacement, explicitly say that the source video's camera, framing, timing, choreography, environment, cuts, and audio are retained, while only the specified subject identity/appearance is transferred. Explicitly prohibit extra people, props, background changes, new actions, or altered timing when those are unwanted.

## Source links

- Official R2V guide: https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md
- Official H3 ComfyUI R2V documentation: https://docs.comfy.org/tutorials/video/minimax/minimax-h3
- Character-swap example: https://www.reddit.com/r/StableDiffusion/comments/1vgtv04/comment/p200b10/
- Community prompt discussion: https://www.reddit.com/r/StableDiffusion/comments/1vgtv04/
