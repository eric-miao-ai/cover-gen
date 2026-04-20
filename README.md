# cover-gen

[简体中文](README.zh-CN.md) | English

A Codex skill that turns natural-language content into consistent cartoon-style illustration prompts.

Instead of forcing the user to manually specify `scene`, `character`, `action`, and `mood`, this skill reads the content first, extracts the likely visual ingredients, and then assembles a stable prompt for image generation.

It works especially well for:

- X/Twitter post covers
- technical article cover images
- technical editorial illustrations
- short scene-based cartoon prompts

## What It Does

The skill follows this workflow:

1. Read the content
2. Infer the use case
3. Extract likely scene, character, action, mood, and visual focus
4. Apply a consistent cartoon style system
5. Build a reusable prompt file
6. Hand the final prompt to Codex image generation

This gives you a better balance of automation and consistency than writing a fresh prompt from scratch every time.

## Repository Layout

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── cartoon-style-system.md
│   └── content-extraction.md
├── examples/
│   ├── twitter-cover-example.md
│   ├── tech-article-example.md
│   └── scene-illustration-example.md
├── README.md
├── README.zh-CN.md
└── LICENSE
```

## Installation

Copy this folder into your Codex skills directory:

```bash
cp -R cover-gen ~/.codex/skills/
```

If your Codex setup uses a different skills directory, copy it there instead.

## Invocation

Use the skill explicitly:

```text
Use $cover-gen to turn this post into a cartoon-style illustration prompt.
```

Or ask naturally with the skill mentioned:

```text
Use $cover-gen 帮我生成一张 Codex 和 Claude Code 测评文章的封面图。
```

## Example Inputs

### 1. Twitter cover

```text
Use $cover-gen 生成一张推文封面图，内容是：codex 的生图功能真的是太好用了。
```

Expected behavior:

- infer `twitter-cover`
- choose a strong focal subject
- emphasize delight and surprise
- generate a clean editorial cartoon cover

### 2. Technical article cover

```text
Use $cover-gen 帮我生成一张 Codex 和 Claude Code 测评的技术文章封面图。
```

Expected behavior:

- infer `tech-article`
- choose comparison composition
- add screens, code panels, benchmark cues, and reviewer energy

### 3. Scene illustration

```text
Use $cover-gen 生成一张卡通图：图书馆里一个女孩正在看电脑查资料，氛围专注安静。
```

Expected behavior:

- infer `scene-illustration`
- preserve the explicit library setting
- keep the same house cartoon style

## Design Principles

- Analyze content before drawing
- Prefer natural language input over rigid parameter forms
- Keep a consistent cartoon visual family
- Let explicit user details override inferred defaults
- Keep prompts reproducible by saving the final assembled prompt

## Notes

- The skill does not depend on a single image backend.
- The skill is strongest when paired with Codex image generation.
- Reference images can be used as style anchors, but the skill still translates them into words for stability.

## License

MIT. See [LICENSE](LICENSE).
