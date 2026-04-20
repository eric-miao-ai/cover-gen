# cover-gen

一个 Codex skill，用来把自然语言内容转换成风格稳定的卡通插画 prompt。

它不是让用户手动填写 `scene`、`character`、`action`、`mood` 这类参数，而是先读取内容，再自动提取合适的画面信息，最后组装成可复用的出图提示词。

它尤其适合这些场景：

- X/Twitter 推文封面图
- 技术文章封面图
- 技术评论类插画
- 简短场景型卡通插图

## 中文说明

### 它做什么

这个 skill 的工作流是：

1. 读取内容
2. 判断用途
3. 提取角色、场景、动作、情绪、画面重点
4. 套用统一卡通风格系统
5. 生成可复用的 prompt 文件
6. 把最终 prompt 交给 Codex 的生图能力

这样做比每次从零写 prompt 更稳定，也更适合持续产出同一视觉系统下的封面图和配图。

### 仓库结构

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
└── LICENSE
```

### 安装

把这个目录复制到你的 Codex skills 目录：

```bash
cp -R cover-gen ~/.codex/skills/
```

如果你的 Codex 使用的是别的 skills 路径，复制到对应目录即可。

### 调用方式

显式调用：

```text
Use $cover-gen to turn this post into a cartoon-style illustration prompt.
```

也可以直接自然语言调用：

```text
Use $cover-gen 帮我生成一张 Codex 和 Claude Code 测评文章的封面图。
```

### 示例输入

#### 1. 推文封面图

```text
Use $cover-gen 生成一张推文封面图，内容是：codex 的生图功能真的是太好用了。
```

预期行为：

- 推断为 `twitter-cover`
- 选择一个强主视觉主体
- 强化“惊喜感”和“好用到超预期”的情绪
- 生成干净、可传播的卡通封面图

#### 2. 技术文章封面图

```text
Use $cover-gen 帮我生成一张 Codex 和 Claude Code 测评的技术文章封面图。
```

预期行为：

- 推断为 `tech-article`
- 选择对比式构图
- 加入屏幕、代码面板、评测线索和技术媒体封面感

#### 3. 场景插图

```text
Use $cover-gen 生成一张卡通图：图书馆里一个女孩正在看电脑查资料，氛围专注安静。
```

预期行为：

- 推断为 `scene-illustration`
- 保留“图书馆”这一明确场景
- 维持统一的卡通视觉风格

### 设计原则

- 先分析内容，再画图
- 优先自然语言输入，而不是参数表单
- 保持统一的卡通视觉体系
- 用户显式提供的信息优先于默认推断
- 最终 prompt 要可复现、可保存

### 备注

- 这个 skill 不绑定某一个图像模型后端
- 它和 Codex 生图能力配合时效果最好
- 即使提供参考图，skill 也会先把风格翻译成文字约束，以提高稳定性

## English

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
