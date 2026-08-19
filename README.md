# Nano Banana Shoe Prompter

[中文](#中文) · [English](#english)

## 中文

`nano-banana-shoe-prompter` 是一个面向 Codex 的个人技能，用于分析鞋类模特参考图，并为 Nano Banana 2 与 Nano Banana Pro 编写可直接复制的单次成图提示词。

### 核心规则

- 锁定参考图中的人物身份、鞋款、服装、场景和摄影系统；
- 每次重新生成都使用原始参考图，生成图只用于诊断；
- 每条提示词完整独立，不依赖上一条提示词或生成结果；
- 每个镜头只设置一个主要视觉目标，并按目标选择姿势、机位和镜头特征；
- 默认输出同一镜头的 Nano Banana 2 与 Nano Banana Pro 两个版本；
- Pro 仅为会改变空间、遮挡、产品还原或优先级决策的部分增加细节；
- 输出前删除重复语义并检查人体、场景结构、镜头与产品要求是否冲突。

技能只编写提示词；除非用户另行要求，否则不会直接生成图片。

### 输出计数

- `1 个镜头/姿势/方案`：默认生成两个提示词版本。
- `10 组姿势方案`：共 10 个镜头、20 条提示词。
- `10 条提示词`：总数就是 10 条；模型分配不清楚时会先确认。

### 安装

将整个文件夹复制到：

```text
$CODEX_HOME/skills/nano-banana-shoe-prompter
```

Windows 常见位置：

```text
C:\Users\<用户名>\.codex\skills\nano-banana-shoe-prompter
```

安装后重新打开任务或刷新 Codex。

### 使用示例

单镜头：

```text
使用 $nano-banana-shoe-prompter 分析这张原始参考图，并分别生成 Nano Banana 2 与 Nano Banana Pro 的完整单次成图提示词。
```

多镜头：

```text
使用 $nano-banana-shoe-prompter，根据这张原始参考图设计 10 组不同姿势的镜头方案。每组分别输出 Nano Banana 2 与 Nano Banana Pro 版本，共 20 条完整提示词。
```

诊断：

```text
使用 $nano-banana-shoe-prompter 比较原始参考图和生成结果，说明达成之处与主要偏差，并分别给出 Nano Banana 2 与 Nano Banana Pro 的全新完整提示词；仍使用原始参考图重新生成。
```

### 文件

- `SKILL.md`：核心工作流与输出规则；
- `references/prompt-patterns.md`：按需读取的镜头与构图模式；
- `references/diagnosis.md`：按需读取的结果、思考过程和对照测试诊断规则；
- `agents/openai.yaml` 与 `assets/`：技能展示信息和图标。

这是独立制作的社区技能，与 Google 或 Nano Banana 官方没有隶属或背书关系。

---

## English

`nano-banana-shoe-prompter` is a personal Codex skill that analyzes footwear-model references and writes copy-ready, single-pass prompts for Nano Banana 2 and Nano Banana Pro.

### Core rules

- Preserve the referenced identity, exact footwear, outfit, scene, and photographic system.
- Start every retry from the original reference; generated images are diagnosis-only.
- Make every prompt complete and independent of previous prompts or results.
- Give each shot one dominant objective and choose pose, camera, and lens character accordingly.
- Return aligned Nano Banana 2 and Nano Banana Pro versions by default.
- Add Pro detail only when it changes a spatial, occlusion, product-fidelity, or priority decision.
- Remove repeated meaning and resolve conflicts before output.

The skill writes prompts and does not generate images unless the user separately requests generation.

### Counting outputs

- `1 shot/pose/concept` produces two prompt versions by default.
- `10 shot concepts` produce 10 shots and 20 prompt blocks.
- `10 prompts` means 10 prompt blocks in total; the skill asks when model allocation is unclear.

### Installation

Copy the full folder to:

```text
$CODEX_HOME/skills/nano-banana-shoe-prompter
```

Typical Windows location:

```text
C:\Users\<username>\.codex\skills\nano-banana-shoe-prompter
```

Reopen the task or refresh Codex after installation.

### Examples

Single shot:

```text
Use $nano-banana-shoe-prompter to analyze this original reference and return complete Nano Banana 2 and Nano Banana Pro prompts for the same shot.
```

Shot set:

```text
Use $nano-banana-shoe-prompter to design 10 distinct pose concepts from this original reference. Return Nano Banana 2 and Nano Banana Pro versions for each concept, for 20 complete prompts total.
```

Diagnosis:

```text
Use $nano-banana-shoe-prompter to compare the original reference and generated result, report what worked and the main drift, then return fresh complete Nano Banana 2 and Nano Banana Pro prompts to use with the original reference.
```

### Files

- `SKILL.md`: core workflow and output rules;
- `references/prompt-patterns.md`: conditional shot and composition patterns;
- `references/diagnosis.md`: result, reasoning-trace, and controlled-comparison diagnosis;
- `agents/openai.yaml` and `assets/`: UI metadata and icons.

This is an independent community skill and is not affiliated with or endorsed by Google or the Nano Banana team.
