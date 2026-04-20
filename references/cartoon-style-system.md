# Cartoon Style System

Use this style system as the default visual family for every image generated with this skill.

## Core Look

- clean cartoon illustration
- crisp dark outlines
- simplified facial features with expressive eyebrows and eyes
- flat colors with soft, limited shading
- warm, gentle indoor-light palette by default
- polished but not glossy
- modern editorial clarity rather than childish sticker art

## Subject Treatment

- Keep characters stylized and readable.
- Use slightly exaggerated expression to show focus, frustration, curiosity, or excitement.
- Avoid realistic skin texture, detailed pores, cinematic lens blur, or 3D render lighting.
- Favor simple clothing shapes and clear silhouettes.

## Environment Treatment

- Keep backgrounds supportive, not dominant.
- Use desks, screens, books, benches, stadium seating, trees, whiteboards, or room dividers as clean scene signals.
- Simplify background objects so the subject stays primary.
- Add only the minimum props needed to clarify the context.

## Technical Visual Language

When the content is technical, introduce selected supporting elements:

- monitors and laptops
- code windows and terminal panels
- architecture blocks and arrows
- document cards, tabs, notes, and diagrams
- server, API, workflow, or model symbols

Render them as part of the same cartoon world. Do not switch to realistic UI screenshots.

## Composition Guidance

### `character-focus`

- One large subject occupying roughly half to two-thirds of the frame
- Minimal supporting environment
- Strong facial expression

### `character-with-ui`

- Subject plus one or two clear interface or tool elements
- Keep the UI readable as shapes and panels, not as tiny dense text
- Use the screen or floating cards to reinforce the article topic

### `character-with-concepts`

- Surround the subject with simplified blocks, arrows, labels, branching paths, or symbolic objects
- Emphasize relationships rather than detail

### `comparison-scene`

- Split the frame into two states or two approaches
- Keep style and character family consistent on both sides
- Make the contrast legible at a glance

## Color Direction

Default direction:

- warm neutrals in the background
- navy, slate, muted blue, and soft accent colors for clothing and UI
- controlled saturation

Allow context-driven changes:

- library -> soft beige, wood, muted book tones
- stadium -> cooler open-air tones, stronger contrast
- park -> greens and warm daylight accents
- night desk -> deeper blues and gentle warm monitor glow

Avoid loud neon palettes unless the content explicitly calls for them.

## Prompt Language

When describing the style in a final prompt, use phrases like:

- consistent clean cartoon illustration style
- expressive stylized character design
- crisp outline drawing with soft flat shading
- simple modern environment details
- readable composition with a strong focal subject

## Negative Constraints

Always avoid:

- photorealistic rendering
- glossy 3D characters
- anime sparkle effects unless explicitly requested
- over-detailed backgrounds
- random decorative clutter
- unreadable small text blocks
- stock-photo realism
