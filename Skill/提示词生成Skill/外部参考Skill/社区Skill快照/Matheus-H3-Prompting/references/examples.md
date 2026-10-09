# Prompt Examples

These examples are intentionally compact. The skill should expand them only when the requested duration and complexity justify it.

## T2VA: single cinematic shot

```text
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a medium close-up frames a lone cyclist stopped beneath a glass bus shelter during heavy rain. The camera holds a static shot as she checks the cracked screen of her phone, looks toward the empty road, and quietly says: <d>[English] It should have arrived by now.</d> A bus headlight appears in the distance and grows brighter without a cut.

overall_soundscape: Heavy rain strikes the glass roof while water runs along the curb. Tires hiss on wet asphalt, the cyclist's jacket rustles, and her breath is barely audible.

non_diegetic_music: Sparse low piano notes at a slow tempo with a restrained cello drone that rises slightly as the headlights approach.
```

## I2VA: preserve the input image

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, the woman in <Picture 1> remains seated at the window table with the same hairstyle, cream sweater, mug position, warm side lighting, and café layout. The camera pushes in with small amplitude at slow speed as she notices the steam forming a heart shape above the mug, smiles, and turns her eyes toward the window. The heart-shaped steam disperses naturally while she lifts the mug with both hands.

overall_soundscape: Quiet café room tone continues under the soft clink of ceramic and a distant espresso machine. Rain taps the window and fabric shifts as she moves.

non_diegetic_music: Gentle fingerpicked acoustic guitar at a slow tempo with a soft sustained pad entering near the end.
```

## R2V: strict character replacement

```text
subject_definitions:
<Subject 1> is the masked red-and-black superhero shown in <Picture 1>, including the suit, mask, crossed sword handles, utility belt, and gloves.
<Video 1> is the source video whose camera framing, handheld drift, plaza setting, choreography, cuts, and timing are retained.
<Audio 1> is the synchronized outdoor ambience and music from <Video 1>, reused in the target video.

summary: [video editing + reference generation + audio reuse] The target video is an edited version of <Video 1> in which only the performer's visual identity is replaced by <Subject 1>. The camera, plaza, mural, choreography, timing, cuts, and original audio remain unchanged.

retention_analysis:
<Subject 1> (appears throughout [Shot 1]): attribute_transfer - the subject's identity, suit, mask, belt, gloves, and sword handles replace the original performer while following the same body positions and actions.
<Video 1> (camera, setting, choreography, cuts, and timing): fully_preserved - every framing change, handheld movement, environment detail, and action beat remains unchanged.
<Audio 1>: fully_copy - the source ambience and music remain the final audio track.

detailed_description:
The target video is a single continuous documentary-style handheld shot in an overcast urban plaza. [Shot 1] <Subject 1> occupies the original performer's exact position and follows the original choreography, including the spin, raised arm, double pointing gesture, crossed-arm stance, turn toward the mural, and final walk away from camera. The plaza, teal mural, notice boards, lighting, camera drift, motion blur, shot timing, and empty background remain unchanged. No extra people, props, cuts, actions, or background elements are introduced. <Audio 1> continues throughout.

overall_soundscape: <Audio 1> is reused as the complete outdoor ambience, including footsteps, clothing movement, and distant city noise.

non_diegetic_music: <Audio 1> is reused as the audience-only music track without alteration.
```
