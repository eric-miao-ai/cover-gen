---
name: cover-gen
description: Generate cartoon-style illustrations from user-provided content such as X/Twitter posts, blog drafts, technical articles, summaries, and short scene descriptions. Use when Codex should read the content, extract the likely character, scene, action, mood, and visual focus automatically, then assemble a stable illustration prompt in a consistent cartoon style for covers, technical article images, or editorial visuals.
---

# Cover Gen

Generate images by analyzing the user's content first. Do not ask the user to fill a parameter form unless the request is genuinely ambiguous and the missing detail changes the result in a major way.

## Workflow

1. Read the input content and infer its use case:
   - `twitter-cover`: hook-driven cover for a post, thread, or opinion piece
   - `tech-article`: explanatory image for a technical article or tutorial
   - `tech-editorial`: conceptual illustration for engineering culture, tooling, AI, workflow, or industry commentary
   - `scene-illustration`: direct illustration of a short scene description
2. Extract the visual ingredients. Read [references/content-extraction.md](references/content-extraction.md).
3. Apply the house style. Read [references/cartoon-style-system.md](references/cartoon-style-system.md).
4. Build a final prompt file before any generation:
   - Save under `prompts/NN-[use-case]-[slug].md`
   - Keep the full final prompt in the file as the reproducibility record
5. Generate with whatever image-generation tool is available in the current runtime.
   - Prefer the runtime's built-in image tool if one exists
   - If multiple backends are available, ask once which backend to use
   - If the user provided a reference image in the current turn, pass it as a reference when the backend supports that
6. Return a short summary of the extracted scene, character, and chosen composition together with the generated image path or result.

## Extraction Rules

- Infer `scene`, `character`, `action`, `mood`, `visual_focus`, and `tech_elements` from the content instead of asking the user to specify them manually.
- Prefer evidence from the content itself over generic defaults.
- When the content is sparse, infer only what is needed to produce a coherent image.
- When the user explicitly names a scene or character, treat that as authoritative.
- When no clear scene exists, choose a setting that fits the content:
  - technical article -> office, desk, terminal, whiteboard, meeting room, or abstract architecture space
  - thread/opinion post -> strong single-subject cover scene
  - study/learning topic -> library, classroom, study desk, or laptop corner
- When no character is clear, use a simple stylized protagonist rather than a highly specific identity.

## Composition Rules

Choose one composition mode and stick to it:

- `character-focus`: one clear subject, large silhouette, minimal environment
- `character-with-ui`: subject plus monitor, terminal, code cards, or floating interface panels
- `character-with-concepts`: subject plus diagrams, modules, arrows, systems, or symbolic elements
- `comparison-scene`: two states, tools, or ideas contrasted left vs right

Use these defaults:

- `twitter-cover` -> `character-focus` unless the content is explicitly comparative
- `tech-article` -> `character-with-ui` or `character-with-concepts`
- `tech-editorial` -> `character-with-concepts`
- `scene-illustration` -> whichever mode best preserves the described scene

## Prompt Construction

Every prompt file should use this shape:

```markdown
# Input Summary
Use case:
Source summary:
Key phrases:

# Extracted Visual Plan
Scene:
Character:
Action:
Mood:
Visual focus:
Tech elements:
Composition mode:
Aspect ratio:

# Style Anchor
[Apply the house style from references/cartoon-style-system.md]

# Image Instructions
[One coherent final image brief in natural language]

# Negative Constraints
- no photorealism
- no 3D render look
- no messy stock-photo composition
- no random unreadable text
- no neon cyberpunk glow unless the content explicitly asks for it
```

Write the final image brief as one clean paragraph, not a keyword dump.

## Use-Case Guidance

### `twitter-cover`

- Prioritize a strong hook and immediate readability.
- Use one main subject and one clear idea.
- Prefer `16:9` or `3:2`.
- Avoid dense labels and tiny text.

### `tech-article`

- Prioritize clarity and explanation over spectacle.
- Show development tools, architecture elements, code blocks, terminals, diagrams, arrows, or labeled modules when the content calls for them.
- Prefer `16:9`, `4:3`, or `3:2`.
- Keep visual hierarchy clean and avoid clutter.

### `tech-editorial`

- Lean more conceptual than instructional.
- Use metaphors that fit engineering or product work: branching paths, layered systems, switching tools, debugging loops, collaboration, review, automation.
- Preserve the same cartoon family so the illustrations feel consistent across posts.

### `scene-illustration`

- Preserve the user's explicit scene first.
- Use the house style, but let the scene description drive the background and props.

## Reference Images

If the user provides a reference image:

- Extract the style cues in words even if the backend supports reference images.
- Treat the reference as a style anchor, not as a command to copy every detail literally.
- Reuse the reference's line quality, simplification level, facial treatment, and color softness.
- Allow scene, pose, props, and composition to change to fit the content.

## Output Discipline

- Do not invent unnecessary lore, outfits, or worldbuilding.
- Do not overfit every request into "a person at a computer" if the content suggests a different scene.
- Do not force scene enums. Unknown scenes should be described naturally and incorporated into the final prompt.
- Keep the style family consistent across different topics so the user's images feel like one visual system.

## References

- Read [references/content-extraction.md](references/content-extraction.md) when deciding what to pull from the input.
- Read [references/cartoon-style-system.md](references/cartoon-style-system.md) when building the final prompt.
