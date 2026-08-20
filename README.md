# Nano Banana Shoe Prompter

[中文](#中文) · [English](#english)

## 中文

`nano-banana-shoe-prompter` 是一个面向 Codex 的个人技能，用于分析鞋类模特参考图，并为 Nano Banana 2 与 Nano Banana Pro 编写可直接复制的单次成图提示词；它也支持使用“彩色原始参考图＋完整黑白构图线稿”重新构建镜头。

### 参考图路由

- 只有一张或多张彩色参考照片、没有完整构图线稿：由技能主动设计并明确描述机位、姿势、构图和鞋履展示方式。
- 同时提供完整黑白构图线稿和彩色原始图：进入完整线稿路线；线稿已经明确的机位、姿势和空间布局不再转写成文字，只补充真实歧义和关键鞋履可读性要求。
- 骨架、人体局部草图或缺少目标画幅与支撑布局的线稿不触发完整线稿路线，只作为局部提示使用。
- 路由依据参考图的语义角色，而不是图片数量；两张普通照片仍属于彩色参考路线。
- 完整线稿路线默认使用“优先级句＋一句角色锚点”；开头已写明成片类型时不再添加通用质量句，也不会为了让提示词脱离参考图仍可理解而复述图中内容。只有具体未决歧义、用户明确要求或已经诊断出的失败才补充细节。
- 用户未指定数值比例时，完整线稿路线写“保持图1原始画幅比例和方向”，不再猜测具体比例数值。

### 核心规则

- 锁定参考图中的人物身份、鞋款、服装、场景和摄影系统；
- 每次重新生成都使用原始参考图，生成图只用于诊断；
- 每条提示词完整独立，不依赖上一条提示词或生成结果；
- 用户同时提供完整黑白构图线稿和彩色原始图时，线稿只控制目标画幅、机位、构图、人物位置与尺度、姿势、遮挡、支撑、双鞋位置和它实际表达的空间布局；彩色原始图是人物、服装、准确鞋款、配饰、道具、场景物体、设计、材质、颜色、光线与摄影质感的权威来源；
- AI 线稿不是内容清单：线稿遗漏的彩色原图内容仍需保留，线稿多画或误画的内容不能覆盖彩色原图；需要精确复现线稿空间时，只在提示词开头声明一次强空间优先级；
- 完整线稿模式会按线稿空间重新构建彩色原图中的同一场景，不同时冻结彩色原图原有的相机、裁切、背景透视或物体坐标；
- 每个镜头只设置一个主要视觉目标，并按目标选择姿势、机位和镜头特征；
- 多镜头通过支撑状态、躯干方向、腿部动作和鞋履展示目标产生实质差异，不以左右镜像或单纯改变机位充数；
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

彩色原始图加完整黑白构图线稿：

```text
使用 $nano-banana-shoe-prompter，以彩色原始图作为人物、服装、鞋款、场景外观和摄影质感参考，以完整黑白线稿作为目标机位、构图、人物姿势、支撑关系和主要场景布局参考，生成完整独立的 Nano Banana 2 与 Nano Banana Pro 提示词。
```

### 文件

- `SKILL.md`：核心工作流与输出规则；
- `references/prompt-patterns.md`：按需读取的镜头与构图模式；
- `references/pose-system.md`：按需读取的姿势决策、场景兼容与多镜头去重规则；
- `references/pose-reference.md`：按需读取的彩色原图与完整黑白构图线稿双参考工作流；
- `references/diagnosis.md`：按需读取的结果、思考过程和对照测试诊断规则；
- `agents/openai.yaml` 与 `assets/`：技能展示信息和图标。

这是独立制作的社区技能，与 Google 或 Nano Banana 官方没有隶属或背书关系。

---

## English

`nano-banana-shoe-prompter` is a personal Codex skill that analyzes footwear-model references and writes copy-ready, single-pass prompts for Nano Banana 2 and Nano Banana Pro. It also supports recomposing a shot from a color original plus a complete black-and-white composition line drawing.

### Reference routing

- With one or more color photographs and no complete composition drawing, the skill designs and explicitly describes the camera, pose, composition, and footwear presentation.
- With both a complete black-and-white composition drawing and a color original, the complete-line-art route applies: camera, pose, and spatial layout already clear in the drawing are not transcribed into prose; only genuine ambiguity and critical footwear-readability decisions are added.
- A skeleton, body-only sketch, or drawing without the target frame and support layout does not trigger the complete-line-art route and is used only as partial guidance.
- Routing follows semantic reference roles rather than image count; two ordinary photographs remain in the content-reference route.
- The complete-line-art route defaults to a priority sentence plus one short role anchor. When the opening already names the output type, it adds no generic quality sentence and does not restate visible content to make the prompt understandable without its references. Extra detail is added only for a concrete unresolved ambiguity, an explicit request, or a diagnosed failure.
- When the user does not specify a numeric ratio, the complete-line-art route says to preserve the drawing's original ratio and direction instead of guessing a numeric value.

### Core rules

- Preserve the referenced identity, exact footwear, outfit, scene, and photographic system.
- Start every retry from the original reference; generated images are diagnosis-only.
- Make every prompt complete and independent of previous prompts or results.
- When a complete black-and-white composition drawing and a color original are supplied together, let the drawing control only the target frame, camera, composition, subject placement and scale, pose, occlusion, support, shoe positions, and the spatial layout it actually depicts; treat the color original as authoritative for every person, garment, exact footwear product, accessory, prop, scene object, design, material, color, light, and photographic characteristic.
- An AI line drawing is not a content inventory: content omitted from it remains supported by the color original, while extra or inaccurate drawn content cannot override the color original. When exact spatial adherence is required, state that winning priority once at the start of the prompt.
- Rebuild the same color scene inside the drawing's spatial arrangement instead of also freezing the color original's old camera, crop, background perspective, or object coordinates.
- Give each shot one dominant objective and choose pose, camera, and lens character accordingly.
- Create meaningful shot-set variation through support state, torso direction, leg action, and footwear presentation; mirroring sides or changing only the camera does not count.
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

Color original plus complete black-and-white composition drawing:

```text
Use $nano-banana-shoe-prompter with the color original as the source for the person, outfit, exact footwear, scene appearance, and photographic character, and the complete black-and-white line drawing as the target camera, composition, pose, support, and major scene-layout reference. Return complete standalone Nano Banana 2 and Nano Banana Pro prompts.
```

### Files

- `SKILL.md`: core workflow and output rules;
- `references/prompt-patterns.md`: conditional shot and composition patterns;
- `references/pose-system.md`: conditional pose decisions, scene compatibility, and shot-set deduplication;
- `references/pose-reference.md`: the conditional dual-reference workflow for a color original and a complete black-and-white composition drawing;
- `references/diagnosis.md`: result, reasoning-trace, and controlled-comparison diagnosis;
- `agents/openai.yaml` and `assets/`: UI metadata and icons.

This is an independent community skill and is not affiliated with or endorsed by Google or the Nano Banana team.
