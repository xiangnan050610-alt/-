# Local ComfyUI Guidance

## Workflow mapping

- H3 T2V/I2V/FL2V use the `fl2va` diffusion weights.
- H3 R2V uses separate `ref2va` weights; a T2V/I2V checkpoint is not a substitute.
- H3 has native stereo audio in the generation workflow.
- For a local 24 GB RTX 3090, use the official pruned INT8 ConvRot diffusion model and NVFP4 text encoder before experimental quantizations.

## Practical prompting settings

Prompt quality cannot rescue an overloaded render. For a 5-second local preview, start with one subject, one continuous shot, one reference image, and a simple audio plan. Increase shots and references only after the composition is stable.

For H3, keep output on the native resolution grid and use a lower-resolution generation pass before an LTX spatial upscale. Do not describe an upscale as if it were a new creative shot; the upscaler should preserve motion, timing, and audio. When using LTX after H3, pass the original H3 audio through if the workflow is intended to preserve it rather than regenerate it.

## R2V progression

1. One reference image for identity or style.
2. `ref_image_size=match` for speed and lower memory use.
3. 3–5 seconds at low megapixels.
4. Add a motion reference video only after identity is stable.
5. Add audio references last and explicitly state whether audio is copied or only used as a reference.

## Source links

- H3 ComfyUI workflows and model mapping: https://docs.comfy.org/tutorials/video/minimax/minimax-h3
- LTX ComfyUI integration: https://docs.ltx.io/open-source-model/integration-tools/comfy-ui
- Official H3 model repository: https://huggingface.co/Comfy-Org/MiniMax-H3
