# Nano Banana Shoe Prompter

[中文](#中文) · [English](#english)

## 中文

`nano-banana-shoe-prompter` 是一个面向 Codex 的个人技能，用于分析鞋类模特参考图、按需提供可选择的动作方案，并将选中方案展开为可直接复制的 Nano Banana 2 提示词；Nano Banana Pro 按需提供。它也支持使用“彩色原始参考图＋完整黑白构图线稿”重新构建镜头。

### 参考图路由

- 只有一张或多张彩色参考照片、没有完整构图线稿：在编写完整提示词时，由技能主动设计并明确描述机位、姿势、构图和鞋履展示方式。
- 用户只发送一张图片且没有说明图片角色和所需结果时：先询问它是彩色人物原图、AI 结果图、线稿/姿势参考还是单独产品图，并确认要动作方案还是完整提示词；用户已经说清意图时直接执行，不重复提问。
- 多张图片的角色与结果明确时直接路由；完整线稿加彩色原图默认可直接生成完整 Nano Banana 2 提示词。只有角色或目标确实影响结果且仍不明确时才问一次。
- 选择动作方案路线后，先返回 10 个简短方案；用户回复编号后，将选中方案作为固定镜头简报展开，不擅自改成另一套动作。
- 同时提供完整黑白构图线稿和彩色原始图：进入完整线稿路线；线稿已经明确的机位、姿势和空间布局不再转写成文字，只补充真实歧义和关键鞋履可读性要求。
- 骨架、人体局部草图或缺少目标画幅与支撑布局的线稿不触发完整线稿路线，只作为局部提示使用。
- 路由依据参考图的语义角色，而不是图片数量；两张普通照片仍属于彩色参考路线。
- 完整线稿路线固定保留四层必要信息：空间优先、参考角色、重新构建而非叠加、统一写实且无线稿泄漏。中文提示词的第四层固定为“按图1的构图，以图2的真实摄影质感重建成片，不保留任何线稿或插画效果。”每层只表达一次，不把线稿或彩色原图继续转写成视觉清单；只有具体未决歧义、用户明确要求或已经诊断出的失败才补充细节。
- 用户未指定数值比例时，完整线稿路线写“保持图1原始画幅比例和方向”，不再猜测具体比例数值。

### 核心规则

- 锁定参考图中的人物身份、鞋款、服装、场景和摄影系统；
- 每次重新生成都使用原始参考图，生成图只用于诊断；
- 每条提示词完整独立，不依赖上一条提示词或生成结果；
- 用户同时提供完整黑白构图线稿和彩色原始图时，线稿只控制目标画幅、机位、构图、人物位置与尺度、姿势、遮挡、支撑、双鞋位置和它实际表达的空间布局；彩色原始图决定所有被保留内容的身份、设计、材质、颜色、光线与摄影质感；
- AI 线稿不是内容清单：人物、鞋款、服装以及穿戴、手持、携带等重要关系仍以彩色原图为准，线稿多画或误画的内容不能覆盖彩色原图；无关的偶然背景小物件不必全部塞入新构图；
- 完整线稿模式会按线稿空间重新构建彩色原图中的同一场景，不同时冻结彩色原图原有的相机、裁切、背景透视或物体坐标；
- 每个镜头只设置一个主要视觉目标，并按目标选择姿势、机位和镜头特征；
- 多镜头通过支撑状态、躯干方向、腿部动作和鞋履展示目标产生实质差异，不以左右镜像或单纯改变机位充数；
- 完整提示词默认只输出 Nano Banana 2；只有用户明确要求时才输出 Nano Banana Pro；
- Pro 仅为会改变空间、遮挡、产品还原或优先级决策的部分增加细节；
- 输出前删除重复语义并检查人体、场景结构、镜头与产品要求是否冲突。

技能只编写提示词；除非用户另行要求，否则不会直接生成图片。

### 两阶段动作选择与输出计数

- 单张图片且用途不明：先确认路线，不直接输出动作菜单或完整提示词。
- 明确选择动作探索：输出 10 个简短动作方案，不生成提示词。
- 回复 `3`：将第 3 个方案展开为 1 条完整 Nano Banana 2 提示词。
- 回复 `3、7`：分别展开为 2 条完整 Nano Banana 2 提示词。
- 明确要求 Nano Banana Pro 或两个版本：严格按要求输出；未要求时只输出 Nano Banana 2。
- 明确要求 `10 条完整提示词`：直接按字面输出 10 条，默认均为 Nano Banana 2。

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

单张图片用途不明：

```text
使用 $nano-banana-shoe-prompter 判断这张图片适合走哪条路线；如果我的意图不明确，先让我选择。
```

选中方案：

```text
展开第 3、7 个方案，默认只输出完整的 Nano Banana 2 提示词。
```

诊断：

```text
使用 $nano-banana-shoe-prompter 比较原始参考图和生成结果，说明达成之处与主要偏差，并给出新的完整 Nano Banana 2 提示词；仍使用原始参考图重新生成。
```

彩色原始图加完整黑白构图线稿：

```text
使用 $nano-banana-shoe-prompter，以彩色原始图作为人物、服装、鞋款、场景外观和摄影质感参考，以完整黑白线稿作为目标机位、构图、人物姿势、支撑关系和主要场景布局参考，生成完整独立的 Nano Banana 2 提示词。
```

### 更新日志

#### v0.2.0 — 2026-08-22

- 增加图片角色与输出意图确认门，覆盖彩色人物原图、AI 结果、线稿/姿势参考和单独产品图；明确多图何时直接路由、何时只问一次。
- 单图动作探索改为先给 10 个精简方案，用户选中后再按固定镜头简报展开；完整提示词默认只输出 Nano Banana 2。
- 明确彩色原图的内容权威不等于强制复制所有偶然背景物；保留人物、鞋履、服装及重要使用关系。
- 诊断缺少原始资产时只报告偏差并索取源图，不把 AI 结果当作重试源图。
- 合并重复模型规则，并增加条件性的纯摄影画面处理，避免无意义扩写。

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

`nano-banana-shoe-prompter` is a personal Codex skill that analyzes footwear-model references, offers selectable action concepts on request, and expands selected concepts into copy-ready Nano Banana 2 prompts. Nano Banana Pro is available on request. It also supports recomposing a shot from a color original plus a complete black-and-white composition line drawing.

### Reference routing

- With one or more color photographs and no complete composition drawing, the skill explicitly designs the camera, pose, composition, and footwear presentation when constructing a full prompt.
- With exactly one unexplained image, the skill first confirms whether it is a color person original, AI result, line-art/pose reference, or product-only reference, and whether the user wants action concepts or a complete prompt. Explicit intent bypasses this question.
- Multiple images route directly when their roles and deliverable are clear; a complete drawing plus a color original can proceed directly to a complete Nano Banana 2 prompt. Only decision-critical ambiguity triggers one concise question.
- After the pose-discovery route is selected, the skill returns 10 brief concepts; selected concepts become fixed shot briefs and are expanded without being redesigned.
- With both a complete black-and-white composition drawing and a color original, the complete-line-art route applies: camera, pose, and spatial layout already clear in the drawing are not transcribed into prose; only genuine ambiguity and critical footwear-readability decisions are added.
- A skeleton, body-only sketch, or drawing without the target frame and support layout does not trigger the complete-line-art route and is used only as partial guidance.
- Routing follows semantic reference roles rather than image count; two ordinary photographs remain in the content-reference route.
- The complete-line-art route always retains four necessary layers: spatial priority, reference roles, reconstruction rather than superimposition, and consistently photorealistic output without line-art leakage. Chinese prompts use the fixed fourth-layer sentence `按图1的构图，以图2的真实摄影质感重建成片，不保留任何线稿或插画效果。`; other languages use its semantic equivalent. Each layer appears once without turning either reference into a visual checklist; extra detail is added only for a concrete unresolved ambiguity, an explicit request, or a diagnosed failure.
- When the user does not specify a numeric ratio, the complete-line-art route says to preserve the drawing's original ratio and direction instead of guessing a numeric value.

### Core rules

- Preserve the referenced identity, exact footwear, outfit, scene, and photographic system.
- Start every retry from the original reference; generated images are diagnosis-only.
- Make every prompt complete and independent of previous prompts or results.
- When a complete black-and-white composition drawing and a color original are supplied together, let the drawing control only the target frame, camera, composition, subject placement and scale, pose, occlusion, support, shoe positions, and the spatial layout it actually depicts; use the color original as the authority for the identity and appearance of all retained content.
- An AI line drawing is not a content inventory: preserve the person, footwear, outfit, and important worn, carried, held, or used relationships from the color original, while incidental background items need not all appear and extra or inaccurate drawn content cannot override the color source.
- Rebuild the same color scene inside the drawing's spatial arrangement instead of also freezing the color original's old camera, crop, background perspective, or object coordinates.
- Give each shot one dominant objective and choose pose, camera, and lens character accordingly.
- Create meaningful shot-set variation through support state, torso direction, leg action, and footwear presentation; mirroring sides or changing only the camera does not count.
- Default complete prompts to Nano Banana 2 and return Nano Banana Pro only when explicitly requested.
- Add Pro detail only when it changes a spatial, occlusion, product-fidelity, or priority decision.
- Remove repeated meaning and resolve conflicts before output.

The skill writes prompts and does not generate images unless the user separately requests generation.

### Two-stage action selection and output counting

- One image with ambiguous intent first produces a route question, not concepts or prompts.
- Explicit pose discovery produces 10 brief action concepts and no prompt blocks.
- Replying `3` expands concept 3 into one complete Nano Banana 2 prompt.
- Replying `3, 7` expands both concepts into two complete Nano Banana 2 prompts.
- Follow an explicit request for Nano Banana Pro or both versions; otherwise return Nano Banana 2 only.
- An explicit request for `10 complete prompts` produces 10 prompt blocks, all Nano Banana 2 by default.

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

Ambiguous single-image intake:

```text
Use $nano-banana-shoe-prompter to determine how this image should be used. If my intent is unclear, ask me to choose a route first.
```

Selected concepts:

```text
Expand concepts 3 and 7 into complete Nano Banana 2 prompts.
```

Diagnosis:

```text
Use $nano-banana-shoe-prompter to compare the original reference and generated result, report what worked and the main drift, then return a fresh complete Nano Banana 2 prompt to use with the original reference.
```

Color original plus complete black-and-white composition drawing:

```text
Use $nano-banana-shoe-prompter with the color original as the source for the person, outfit, exact footwear, scene appearance, and photographic character, and the complete black-and-white line drawing as the target camera, composition, pose, support, and major scene-layout reference. Return a complete standalone Nano Banana 2 prompt.
```

### Changelog

#### v0.2.0 — 2026-08-22

- Added an image-role and deliverable gate covering color person originals, AI results, line-art/pose references, and product-only images, with direct routing for clear multi-image requests.
- Changed single-image pose exploration to 10 brief concepts followed by fixed-brief expansion; complete prompts now default to Nano Banana 2 only.
- Clarified that color-source authority does not require every incidental background item to appear, while preserving the person, footwear, outfit, and important use relationships.
- When diagnosis lacks original assets, the skill reports visible drift and requests the sources without treating the AI result as a retry source.
- Consolidated model-selection wording and added conditional clean-photography handling without prohibition-list inflation.

### Files

- `SKILL.md`: core workflow and output rules;
- `references/prompt-patterns.md`: conditional shot and composition patterns;
- `references/pose-system.md`: conditional pose decisions, scene compatibility, and shot-set deduplication;
- `references/pose-reference.md`: the conditional dual-reference workflow for a color original and a complete black-and-white composition drawing;
- `references/diagnosis.md`: result, reasoning-trace, and controlled-comparison diagnosis;
- `agents/openai.yaml` and `assets/`: UI metadata and icons.

This is an independent community skill and is not affiliated with or endorsed by Google or the Nano Banana team.
