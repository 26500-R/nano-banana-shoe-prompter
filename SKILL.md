---
name: nano-banana-shoe-prompter
description: Analyze a footwear-model reference image and write production-ready, single-pass prompts for Nano Banana 2 / Gemini image generation. Use when the user wants new shoe-model poses, camera angles, scene-consistent fashion images, a multi-pose prompt set, or diagnosis of a generated result. Preserve the reference scene and outfit, choose lenses adaptively rather than always using wide angle, and optimize for one generation from the original reference instead of iterative re-editing.
---

# Nano Banana Shoe Prompter

Create prompts for Nano Banana 2; do not generate the image unless the user separately asks for image generation.

## Workflow

1. Inspect every supplied reference and result image visually.
2. Identify the user's intended deliverable: one prompt, a numbered prompt set, or result diagnosis.
3. Infer the scene, outfit, existing photographic language, shoe visibility, and usable environment geometry from the image. Do not inventory these details in the final prompt.
4. Choose one clear visual objective for each image, then match the pose, camera height, lens family, and framing to that objective.
5. Write a standalone, single-pass prompt intended to be submitted with the original reference image.
6. Return no separate negative prompt unless the user explicitly requests one.

## Non-negotiable production rules

- Always start each new shot from the original reference image. Never recommend progressive re-editing of a generated result unless the user explicitly overrides this rule.
- Treat the reference image as the source of truth for the existing outfit, scene, furniture, lighting, color, and photographic character.
- Describe preserved content concisely. Do not restate garment colors, fabrics, collars, cuffs, skirt shapes, shoe construction, furniture style, or wall texture unless the user asks to change that item.
- Never tell the image model that the face or footwear is temporary, unimportant, or destined for later replacement.
- Do not mention local repair, inpainting, face swapping, shoe swapping, or downstream post-production in the generation prompt.
- Do not default to slippers, homes, or any other shoe or scene category. Infer them from the reference and user brief.
- Do not default to wide angle. Select the lens according to the shot objective.
- Give each prompt one dominant visual objective. Avoid competing priorities such as rigid standing, extreme low angle, extreme foreground enlargement, complex furniture interaction, and exact symmetry in the same shot.
- Prefer positive spatial descriptions over lists of prohibitions: state where each foot, hand, prop, and camera should be.
- Keep hands visibly empty and use only existing props when no new accessory is requested.
- Treat overlaid logos, captions, and watermarks as layout elements rather than physical scene content. Do not call them required reference details.

## Lens and pose selection

Choose adaptively:

- 35–50 mm: natural e-commerce presentation, stable standing poses, accurate proportions.
- 28–35 mm: environmental full-body images and mild fashion perspective.
- 20–28 mm: deliberate shoe-hero images, low viewpoints, strong depth, and foreground emphasis.
- 50–85 mm: material details, elegant portraits, and compressed space.
- 70–105 mm: refined fashion compression when the environment allows sufficient distance.

Pair the lens with a compatible pose:

- Strong low-angle wide shots: favor seated, half-seated, crouched, stepping, or one-leg-extended poses.
- Standard standing shots: favor natural or mild wide angles unless the user explicitly prioritizes extreme perspective.
- High-angle shots: describe visible evidence such as the top of the head, shoulders, shoe uppers, and a larger floor area.
- Shoe close-ups: protect complete shoe contours, foot-ground contact, and independent visibility of the hero shoe.

If the user's taste is known, respect it without turning it into a universal rule. A preference for wide angle means use it where it strengthens the image, not in every shot.

## Aspect ratio selection

Resolve the output ratio in this order:

1. Use the user's explicitly requested aspect ratio and orientation.
2. If the user gives no ratio, preserve the original reference image's aspect ratio and orientation.
3. Only when the reference ratio cannot be determined reliably, choose by intended use: 3:4 or 4:5 for full-body commerce, 4:5 for social portrait posts, 9:16 for mobile vertical content, 16:9 or 3:2 for horizontal environmental advertising, and 1:1 for square product presentation.

Do not hard-code `3:4` or any other ratio into every prompt. State a numeric ratio only when the user requests it or when intentionally changing an unusable or unknown source ratio. Otherwise write:

> 保持与原始参考图片相同的画幅比例和画面方向。

## Prompt construction

Build each prompt in this order:

1. **Reference anchor** — create a new photograph from the same shoot and preserve the existing visual system.
2. **Single hero objective** — name the one outcome that should dominate model selection.
3. **Pose geometry** — body direction, weight-bearing leg, hand placement, and explicit left/right or foreground/background foot positions.
4. **Camera** — direction, height, lens family, distance, and tilt.
5. **Composition** — resolve aspect ratio with the rules above, then define crop, foreground/midground/background positions, and visible floor around the shoes.
6. **Completion criteria** — natural anatomy, ground contact, clean shoe contours, and preservation of the reference visual system.

Use concise natural Chinese. Detail the requested change; summarize what must remain. For complex shots, use short ordered paragraphs rather than a long rule list.

Use this preservation sentence as a base and adjust only when necessary:

> 请基于所提供的原始参考图片，创建同一拍摄系列中的一张全新照片。延续参考图片中人物现有的服装与整体造型，以及原场景、光线、色调和摄影质感；参考图用于确定这些现有视觉内容，不根据文字重新设计它们。

## Priority design

State priorities only when the model must choose between competing goals. Align them with the user's actual taste. A useful default for creative shoe imagery is:

1. Reference scene and outfit continuity.
2. Shoe presentation and commercial usability.
3. Camera language and composition.
4. Natural, compelling body language.
5. Literal pose labels such as standing or sitting.

For standard catalog images, move proportion accuracy and literal pose compliance above dramatic camera language.

## Output behavior

- For one prompt: return a short shot title and one copy-ready code block.
- For a set: return numbered, independent prompts; every prompt must be usable with the original reference image without relying on previous outputs.
- For result diagnosis: compare the result with the stated hero objective, identify what worked and drifted, then revise the generator rules or offer a fresh one-pass prompt from the original reference. Do not recommend editing the result again.
- Ask a question only when shoe category, intended use, or desired visual style would materially change the result and cannot be inferred.

Read [references/prompt-patterns.md](references/prompt-patterns.md) when a concrete camera/pose pattern or a multi-shot mix is needed.
