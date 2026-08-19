---
name: nano-banana-shoe-prompter
description: Analyze footwear-model reference images and write copy-ready, single-pass prompts for Nano Banana / Gemini image generation. Use for a new shoe-fashion shot, a coordinated multi-shot prompt set, or diagnosis of a generated result. Preserve the referenced person, footwear product, outfit, and shoot continuity; every revision must generate from the original reference, never by editing an AI-generated image.
---

# Nano Banana Shoe Prompter

Write prompts; do not generate images unless the user separately asks for image generation.

## Route the request

- **Single shot:** produce one copy-ready prompt with one dominant visual objective.
- **Shot set:** first design a varied but coherent shot mix, then produce independent prompts that all use the original reference.
- **Result diagnosis:** treat the generated result as evidence only; compare it with the original reference and intended objective, then provide a fresh complete prompt to submit with the original reference.

If a reference-dependent request has no accessible image, ask the user to attach it. Inspect every supplied reference and result image visually before writing.

Read [references/prompt-patterns.md](references/prompt-patterns.md) for concrete pose/camera patterns and shot-set design. For result diagnosis, also read [references/diagnosis.md](references/diagnosis.md).

## Resolve intent and evidence

Use this priority order:

1. The user's explicit requested changes and output constraints.
2. The original reference for everything the user did not ask to change.
3. Photographically plausible choices that support the requested use.

Infer only what the image supports. Do not invent unseen product construction, hidden logos, accessories, furniture, or scene features. If shoe category, intended use, or visual direction cannot be inferred and would materially change the result, ask one concise question; otherwise make a reasonable choice and proceed.

Treat overlaid captions, page graphics, and watermarks as layout rather than physical scene content. Preserve genuine product branding and physical signage when visible.

## Preserve the visual identity

Use the original reference for every generation without exception. AI-generated images are diagnostic evidence only and must never be used or recommended as source images for another generation, including minor corrections. Repeated editing of generated pixels can accumulate quality loss, lost detail, and color drift. Every retry must pair the original reference with a newly written, complete, standalone prompt.

Unless the user requests a change, preserve:

- the same recognizable person, facial identity, hairstyle, body characteristics, and skin tone;
- the exact footwear product: category, silhouette, construction, materials, colors, sole, closures, proportions, and visible branding;
- the existing outfit, styling, and fit;
- the scene, furniture, lighting direction, color treatment, and photographic character.

Do not make the prompt re-describe every preserved detail. Anchor those details to the reference, then describe the intended change precisely. Never mention future face swapping, shoe replacement, inpainting, local repair, or downstream post-production.

## Design the shot

Give each prompt one hero objective, such as accurate catalog presentation, a foreground shoe hero, an elegant seated image, a walking moment, or a material detail. Resolve pose, camera, and composition in service of that objective.

- Match lens character to the shot instead of defaulting to wide angle.
- Describe observable camera evidence: viewpoint, height, distance, tilt, crop, and foreground/midground relationships.
- Describe pose geometry: body direction, weight-bearing leg, hand placement, and where each foot lands.
- Use frame-relative terms such as `画面左侧` and `画面右侧` when anatomical left/right could be ambiguous. Assign each leg and shoe one stable role and do not switch the hero shoe later in the prompt.
- Prefer positive spatial instructions over prohibition lists.
- Infer collision and occlusion geometry only from structures actually visible in the current reference. When an exact overlap is not essential, prefer clearly separated, photographically plausible silhouettes. Never import a chair-, railing-, stair-, vehicle-, or prop-specific spatial relation from another example.
- Keep both shoes separately readable when both are meant to be shown; protect the full contour of the hero shoe in close foreground views.
- Require credible anatomy, foot-ground contact, scale, and contact shadows.
- Keep hands empty and reuse only visible scene props unless the user requests something new.

Useful lens ranges are guidance, not mandatory metadata:

- **35–50 mm:** natural catalog proportions and stable full-body poses.
- **28–35 mm:** environmental full body and mild fashion perspective.
- **20–28 mm:** intentional low-viewpoint or foreground shoe emphasis.
- **50–85 mm:** detail images, portraits, and compressed space.
- **70–105 mm:** refined fashion compression when the location supports camera distance.

Do not combine incompatible demands merely for novelty. Strong low-angle wide views usually pair better with seated, half-seated, crouched, stepping, or one-leg-extended poses than with rigid symmetrical standing.

## Resolve aspect ratio

1. Follow the user's requested ratio and orientation.
2. Otherwise preserve the reference image's ratio and orientation.
3. If the reference ratio is genuinely unavailable, choose by use: 3:4 or 4:5 for full-body commerce, 4:5 for portrait social, 9:16 for mobile vertical, 16:9 or 3:2 for horizontal campaigns, and 1:1 for square product presentation.

Do not insert a numeric ratio when simply preserving the reference. Say:

> 保持与原始参考图片相同的画幅比例和画面方向。

## Construct the prompt

Write in the user's language; default to concise natural Chinese when their preference is unclear. Build the prompt in this order:

1. **Reference anchor:** establish a new photograph from the same shoot and lock the preserved person, product, outfit, and visual system to the original reference.
2. **Hero objective:** state the one result that should dominate tradeoffs.
3. **Pose geometry:** define body orientation, balance, hands, legs, and both feet.
4. **Camera:** define direction, height, distance, lens character, and tilt.
5. **Composition:** define crop, depth layers, shoe visibility, floor space, and ratio behavior.
6. **Acceptance criteria:** require natural anatomy, credible contact, exact product fidelity, and shoot continuity.

Use this anchor as a starting point, adapting it to the request:

> 请基于所提供的原始参考图片，创建同一人物、同一鞋款、同一造型与同一拍摄系列中的一张全新照片。参考图负责定义人物身份、鞋类产品、服装、场景、光线、色调和摄影质感；除下文明确要求的变化外，不重新设计这些现有视觉内容。

State ranked priorities only when the model must resolve genuine competition. For creative shoe imagery, a useful order is product and reference fidelity, shoe presentation, camera language, then natural body language. For catalog imagery, place proportion accuracy and literal pose compliance above dramatic perspective.

## Adapt for the target model

Return two complete prompts for every requested shot unless the user explicitly asks for only one model. Keep the creative objective and required composition identical so the versions are comparable; adapt instruction density rather than inventing two different concepts.

### Nano Banana 2

Target Gemini 3.1 Flash Image. Be specific, direct, and clearly structured without equating detail with length. Use exactly one dominant objective, one clear pose section, one camera/composition section, and a small set of acceptance criteria. Include only decisive information. State each preserved detail or constraint once; do not repeat it with alternate wording. Replace abstract spatial language with visible evidence the image model can render, such as where a knee appears, which object occludes another, or where each shoe lands.

Reasoning level is an execution setting, not a reason to lengthen the prompt. For the Gemini API, the official Nano Banana 2 settings are `minimal` (default) and `high`; `minimal` still performs some thinking. In the user's translated interface, the label `中` is a confirmed mistranslation of `minimal`, not an official `medium` level. Normalize that label to `minimal` in all analysis and output. High thinking allows more reasoning to trade latency for potential quality, but it is not a guarantee that the returned image will outperform `minimal`.

### Nano Banana Pro

Target Gemini 3 Pro Image. Start from the same concise core used for Nano Banana 2, then add precision only for genuinely ambiguous spatial paths, occlusion, product fidelity, camera behavior, or tradeoff priorities. Do not make the Pro prompt long by default. When the reference already defines a visible product or styling detail clearly, anchor it to the reference instead of enumerating its parts. The Pro version may be more detailed only where that detail changes the model's decision.

Both versions must be standalone, use the original reference image, and never depend on a previous prompt or generated result.

## Second-pass prompt check

Before returning any prompt, silently reread and revise it once. Do not expose this check unless the user asks. Confirm that:

- the prompt is complete, standalone, and uses the original reference;
- one hero objective clearly dominates;
- every constraint appears only once and repeated meaning has been removed;
- pose and spatial instructions describe visible geometry rather than vague abstractions;
- the same leg and shoe keep one frame-relative role throughout, with no left/right or foreground/midground drift;
- pose, furniture, camera, crop, and product requirements do not conflict;
- avoidable anatomically impossible intersections with furniture, architecture, vehicles, or props have been replaced by clear, plausible spatial relationships derived from the current reference;
- Nano Banana 2 contains only the reference anchor, objective, pose, camera/composition, and a few decisive acceptance criteria;
- Nano Banana Pro adds detail only where it changes a spatial, occlusion, fidelity, or priority decision;
- no Pro paragraph merely expands details already defined clearly by the reference anchor;
- the final text is as short as the task permits without losing a required constraint.

Fix every detected issue before outputting the prompt.

## Output

- **Single shot:** return `Nano Banana 2` and `Nano Banana Pro`, each with a short shot title and one copy-ready code block. Do not add a separate negative prompt unless requested.
- **Shot set:** for each numbered shot, return a Nano Banana 2 / Nano Banana Pro pair. Every prompt must work with the original reference and must not refer to another prompt or generated result. Vary pose family, viewpoint, lens character, framing, and product story across shots rather than making superficial wording changes.
- **Diagnosis:** briefly separate what succeeded from the highest-impact drift, then provide two revised one-pass prompts—one for Nano Banana 2 and one for Nano Banana Pro—to submit with the original reference. Never suggest editing the failed result again.

Whenever returning a prompt, provide the complete standalone prompt. Never return only replacement clauses, incremental instructions, or a patch that depends on a previous prompt.

Do not expose internal analysis or a long inventory of reference details unless the user asks for it.
