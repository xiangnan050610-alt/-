# MiniMax H3 Base Prompting

This reference summarizes the official base prompt contract without reproducing the source document verbatim.

## Shared sections

`integrated_multimodal_description` is the timeline. It should cover style, composition, subjects, actions, reactions, camera, cuts, dialogue, singing, visible text, and synchronized diegetic audio.

`overall_soundscape` is one short paragraph about ambience, physical action sounds, and non-verbal human sounds across the whole clip. Do not repeat dialogue or music here.

`non_diegetic_music` describes only music that the characters cannot hear. Specify instrumentation, tempo, rhythm, and dynamic changes. Use `N/A` when absent.

## T2VA

Start directly with the three shared sections. Establish the overall style and opening composition in `[Shot 1]`. Add later cuts only when they introduce a new viewpoint, space, time, subject state, or information. Prefer camera motion over unnecessary cuts.

Template:

```text
integrated_multimodal_description: [Shot 1] [style], [framing] ... [Shot 2] At 00:04.000, the camera cuts to ...

overall_soundscape: ...

non_diegetic_music: ...
```

## I2VA

The first line must identify the image as the fully referenced frame at `0.00` seconds:

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.
```

Start `[Shot 1]` from the image's actual composition, appearance, lighting, clothing, objects, and spatial relationships. Then describe action onset, continuous development, and the ending state. Do not restart the scene or contradict the image.

## FL2VA

The first line maps the opening and ending images to time. Use the effective duration with two decimal places. Normally keep one continuous shot. Describe intermediate pose, object, camera, lighting, and composition changes that progressively reach the last image.

## L2VA

The first line maps the last image to the effective end time. Infer a plausible earlier state and describe a continuous path that lands on the final image. Do not treat the ending reference as if it were already visible at the beginning.

## Camera vocabulary

Use natural expressions such as `the camera pushes in with small amplitude at slow speed`. Useful motion types include static shot, push in/pull out, zoom, pan, truck, tilt, pedestal, arc, tracking, POV, roll, and slight/strong shake. Add amplitude and speed only when they convey meaningful change.

## Speakers and speech

Give each vocal source a stable `(S1)`, `(S2)` ID and reuse it across shots. Put only the exact spoken words inside `<d>[Language] ...</d>`. For voiceover, explicitly say `in an off-screen voiceover` and state that the on-screen lips remain closed. Use `<scenetrans>` for dialogue continuing over a cut and `<cutoff>` when speech is truncated by the clip ending.

## On-screen text

Put visible signs, labels, subtitles, and UI text in English double quotation marks. Preserve the requested spelling and punctuation exactly. Do not invent microtext.

## Source links

- Official base guide: https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_base_en.md
- Official H3 ComfyUI workflows: https://docs.comfy.org/tutorials/video/minimax/minimax-h3
- Community discussion and examples: https://www.reddit.com/r/StableDiffusion/comments/1vgtv04/comment/p200b10/
