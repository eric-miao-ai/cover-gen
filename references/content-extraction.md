# Content Extraction

Extract only the information that helps produce a better image. Do not force every field to be present.

## Fields

| Field | Meaning | How to infer |
|-------|---------|--------------|
| `use_case` | What the image is for | Post cover, technical article image, editorial concept, direct scene |
| `scene` | Physical or conceptual setting | Explicit user wording first, otherwise infer from the content |
| `character` | Main person or group | Use roles mentioned in the text; otherwise use a generic stylized subject |
| `action` | What the character is doing | Read verbs, tasks, or implied activity |
| `mood` | Emotional tone | Use tone words, stakes, and wording intensity |
| `visual_focus` | The main thing the picture should communicate | Hook, explanation, contrast, process, tension, curiosity |
| `tech_elements` | Supporting artifacts | Laptop, monitor, terminal, whiteboard, architecture blocks, arrows, docs, charts |

## Use-Case Detection

### `twitter-cover`

Signals:

- Mentions of post, thread, X, Twitter, hook, opinion, hot take, launch, announcement
- Short content with a strong thesis
- Needs a cover rather than a full explanation

Visual goal:

- One compelling focal point
- Fast comprehension
- Low text density

### `tech-article`

Signals:

- Tutorial, architecture, distributed systems, caching, workflows, debugging, performance, tools, backend, frontend, AI engineering
- Long-form explanatory content
- Concepts that benefit from diagrams or UI artifacts

Visual goal:

- Clarify the concept
- Show process, tools, or relationships
- Maintain clean hierarchy

### `tech-editorial`

Signals:

- Commentary on engineering culture, tool choice, AI coding, productivity, collaboration, org design, process friction
- Strong point of view without a step-by-step tutorial

Visual goal:

- Use symbolic or metaphorical visual framing
- Keep the character relatable and expressive

### `scene-illustration`

Signals:

- Direct scene instructions such as "在图书馆", "在体育场", "在公园"
- Short prompts centered on setting, role, and action

Visual goal:

- Preserve the scene faithfully
- Keep the cartoon style consistent

## Scene Inference

Use explicit scene wording when present. If not present, infer the simplest fitting environment:

- debugging, coding, architecture, review -> office, desk, workstation, whiteboard room
- learning, reading, studying -> library, study desk, classroom
- collaboration, planning, discussion -> meeting room, cafe table, shared desk
- momentum, competition, sports analogy -> stadium, track, field, training area
- reflection, solitude, creativity -> park bench, quiet cafe, nighttime desk, window seat

If the user names an unfamiliar scene, keep the original phrase and describe it naturally in the prompt. Do not reject it because it is not in a known list.

## Character Inference

Prefer content-specific roles:

- engineer, developer, founder, student, designer, researcher, athlete, team

If only gender or age is implied, use a simple stylized character:

- boy, girl, man, woman, young developer, student

If no character is needed, allow symbolic composition with very light character presence.

## Action Inference

Look for verbs and task cues:

- write code, debug, read docs, compare tools, discuss, explain, sketch, run, train, think, review, present

If the content is conceptual, use a visually legible action:

- looking at a screen, pointing at a diagram, standing between two options, reading notes, discussing with a teammate

## Mood Inference

Use the tone of the input:

- focused
- frustrated
- curious
- confident
- excited
- calm
- reflective
- urgent

Choose one primary mood and at most one secondary nuance.

## Visual Focus

Decide what the viewer should understand in one glance:

- a person wrestling with complexity
- a clear technical system or workflow
- a contrast between old and new tools
- a moment of discovery
- a strong post hook

This field should drive composition more than decorative details do.
