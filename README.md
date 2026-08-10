# Nano Banana Shoe Prompter

[中文](#中文) · [English](#english)

## 中文

`nano-banana-shoe-prompter` 是一个面向 Codex 的个人技能。它能够分析鞋履模特参考图，并生成适合 Nano Banana 2 / Gemini 图像模型的单次成图提示词。

这个技能不会直接生成图片。它负责理解参考图中的场景、服装、人物姿态和摄影语言，再输出一条或一组可复制到 Nano Banana 2 的中文提示词。

### 主要功能

- 识别参考图中的场景、服装、构图、光线和可用空间关系；
- 为鞋履展示选择匹配的姿势、机位、景别和镜头；
- 根据画面目标灵活使用自然透视、广角或中长焦；
- 生成从原始参考图出发的独立单次成图提示词；
- 支持单个镜头、整套多姿势方案和生成结果诊断；
- 默认使用正向空间描述，不输出独立负面提示词；
- 避免向图像模型透露后期换脸、换鞋或局部修复计划；
- 优先保持参考图的场景、服装、光线、色调和摄影质感。

### 设计原则

1. 每个新画面都使用原始参考图，不连续编辑中间生成图。
2. 参考图负责定义已有视觉内容，文字重点描述需要改变的动作和摄影机。
3. 每条提示词只设置一个主要视觉目标，减少互相冲突的要求。
4. 镜头并非固定为广角：标准电商展示可使用自然透视，鞋履主视觉才按需使用强广角。
5. 姿势需要与镜头匹配，例如低机位强广角更适合坐姿、半坐姿、迈步或单腿前伸。

### 安装

将整个 `nano-banana-shoe-prompter` 文件夹复制到 Codex 的个人技能目录：

```text
$CODEX_HOME/skills/nano-banana-shoe-prompter
```

Windows 常见位置：

```text
C:\Users\<用户名>\.codex\skills\nano-banana-shoe-prompter
```

安装后重新打开任务或刷新 Codex，使技能被发现。

### 使用方法

上传一张鞋履模特参考图，然后调用：

```text
使用 $nano-banana-shoe-prompter 分析这张参考图，并生成一条适合 Nano Banana 2 一次成图的鞋履摄影提示词。
```

生成多姿势方案：

```text
使用 $nano-banana-shoe-prompter，根据这张参考图生成 10 条不同姿势的独立提示词。每条都从原始参考图生成，并根据画面目标灵活选择镜头。
```

指定视觉方向：

```text
使用 $nano-banana-shoe-prompter，为这张图生成一个低机位广角鞋履主视觉提示词，突出前景鞋和空间纵深。
```

```text
使用 $nano-banana-shoe-prompter，为这张图生成一个自然透视的标准电商站姿提示词，不使用强广角。
```

诊断生成结果：

```text
使用 $nano-banana-shoe-prompter 分析参考图和生成结果，判断姿势、机位、鞋履展示与场景服装一致性是否达到目标，并重新给出一条从原始参考图生成的单次成图提示词。
```

### 目录结构

```text
nano-banana-shoe-prompter/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    └── prompt-patterns.md
```

### 说明

这是一个独立制作的社区技能，与 Google 或 Nano Banana 官方没有隶属或背书关系。Nano Banana、Gemini 及相关名称属于其各自权利人。

---

## English

`nano-banana-shoe-prompter` is a personal Codex skill that analyzes footwear-model reference images and writes production-ready, single-pass prompts for Nano Banana 2 / Gemini image models.

The skill does not generate images itself. It interprets the scene, outfit, pose, spatial layout, and photographic language of a reference image, then produces one or more Chinese prompts ready to paste into Nano Banana 2.

### Features

- Analyzes the reference scene, outfit, composition, lighting, and usable spatial relationships;
- Selects a suitable pose, camera position, framing, and lens for the footwear objective;
- Chooses natural perspective, wide angle, or telephoto adaptively instead of forcing one lens style;
- Produces independent, single-pass prompts that always start from the original reference image;
- Supports single shots, multi-pose prompt sets, and generated-result diagnosis;
- Uses positive spatial descriptions by default instead of a separate negative prompt;
- Avoids telling the image model about later face swaps, shoe replacement, or local repair;
- Prioritizes continuity of the reference scene, outfit, lighting, color, and photographic character.

### Design principles

1. Start every new shot from the original reference image rather than repeatedly editing generated outputs.
2. Let the reference define existing visual details; use text mainly to describe the requested pose and camera changes.
3. Give each prompt one dominant visual objective to reduce conflicting instructions.
4. Do not force wide angle into every shot: use natural perspective for standard catalog work and stronger wide angle only when it improves the shoe-led composition.
5. Match the pose to the lens. Strong low-angle wide shots often work better with seated, half-seated, stepping, or one-leg-extended poses.

### Installation

Copy the entire `nano-banana-shoe-prompter` folder into your personal Codex skills directory:

```text
$CODEX_HOME/skills/nano-banana-shoe-prompter
```

Typical Windows location:

```text
C:\Users\<username>\.codex\skills\nano-banana-shoe-prompter
```

Reopen the task or refresh Codex after installation so the skill can be discovered.

### Usage

Attach a footwear-model reference image, then invoke:

```text
Use $nano-banana-shoe-prompter to analyze this reference image and write a single-pass footwear photography prompt for Nano Banana 2.
```

Create a multi-pose set:

```text
Use $nano-banana-shoe-prompter to create 10 independent pose prompts from this reference. Start every shot from the original image and choose the lens adaptively for each visual objective.
```

Request a specific visual direction:

```text
Use $nano-banana-shoe-prompter to create a low-angle wide-lens shoe hero prompt with a strong foreground shoe and pronounced spatial depth.
```

```text
Use $nano-banana-shoe-prompter to create a standard e-commerce standing pose with natural perspective and no strong wide-angle effect.
```

Diagnose a result:

```text
Use $nano-banana-shoe-prompter to compare the reference and generated result, evaluate the pose, camera, shoe presentation, scene, and outfit continuity, then write a fresh single-pass prompt to use with the original reference.
```

### Repository structure

```text
nano-banana-shoe-prompter/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    └── prompt-patterns.md
```

### Disclaimer

This is an independent community skill and is not affiliated with or endorsed by Google or the Nano Banana team. Nano Banana, Gemini, and related names belong to their respective owners.
