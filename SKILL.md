---
name: nano-banana-shoe-prompter
description: Analyze footwear-model references and write copy-ready, single-pass prompts for Nano Banana / Gemini image generation, including shots guided by a complete black-and-white composition line drawing plus a color original. Use for a new shoe-fashion shot, a coordinated multi-shot set, line-art-guided recomposition, or diagnosis. Preserve the referenced person, footwear product, outfit, and shoot continuity; never retry from an AI-generated final image.
---

# Nano Banana Shoe Prompter

Write prompts; do not generate images unless the user separately asks for image generation.

## Route the request

- **Single shot:** design one composition with one dominant visual objective.
- **Shot set:** design meaningfully different but visually coherent compositions.
- **Line-art-guided recomposition:** use a color original as the content-and-appearance source and a complete black-and-white line drawing as the target spatial composition.
- **Result diagnosis:** compare the result with the original reference and intended objective, then correct the instruction rather than the failed pixels.

Treat a **shot, pose, or concept** as one composition and a **prompt** as one copy-ready text block. By default, each shot receives a Nano Banana 2 prompt and a Nano Banana Pro prompt. If the user specifies a total number of prompts rather than shots, respect that literal total; ask one concise question only when the requested model allocation is genuinely unclear.

If a reference-dependent request has no accessible image, ask the user to attach it. Inspect every supplied reference and result image visually before writing.

- Read [references/prompt-patterns.md](references/prompt-patterns.md) only when concrete camera, crop, or shot-family guidance is needed.
- Read [references/pose-system.md](references/pose-system.md) when the user requests pose exploration, multiple poses, or body-structure diversity in a shot set.
- Read [references/pose-reference.md](references/pose-reference.md) when the user supplies a complete black-and-white line drawing together with a color original.
- Read [references/diagnosis.md](references/diagnosis.md) when evaluating a generated result, visible reasoning, thought images, prompt-length tests, or reasoning settings.

## Generation invariants

Every attempt must use the user-designated color original. When the shot is guided by a complete line drawing, every attempt must also use that same line drawing. Treat AI-generated final advertising images only as diagnostic evidence and never recommend them as source images for another generation, including minor corrections; repeated editing can accumulate quality loss, lost detail, and color drift. A user-supplied black-and-white line drawing may be used as a secondary spatial-control asset even when it was created by a separate pose-transfer workflow; it is never a source of identity, product, texture, or final-image pixels.

Every delivered prompt must be complete, standalone, and usable with all designated original reference assets without relying on a previous prompt or result.

When the user supplies a color original and a complete black-and-white line drawing, honor their labels and restate both semantic roles inside every standalone prompt. The line drawing controls the target frame, crop, camera evidence, subject placement and scale, pose, occlusion, support relationships, shoe locations, and the spatial layout of major drawn scene elements. The color original remains the sole source for identity, body appearance, face, hair, exact footwear, outfit, accessories, scene identity, materials, color, lighting, and photographic character. Do not infer image roles from upload order when the user has identified them.

Unless the user requests a change, preserve the same recognizable person, exact footwear product, outfit and styling, scene identity, lighting character, color treatment, and photographic character. In line-art-guided recomposition, rebuild the color original's scene content within the line drawing's spatial arrangement; do not also demand the color original's old camera, object coordinates, crop, or background perspective. Infer only what the references support; do not invent hidden product construction, logos, accessories, furniture, or scene features.

Anchor preserved content to the reference instead of re-enumerating it. Never mention future face swapping, shoe replacement, inpainting, local repair, or downstream post-production in a generation prompt.

Treat overlaid captions, page graphics, and watermarks as layout rather than physical scene content. Preserve genuine product branding and physical signage when visible.

## Design the shot

Give each shot one hero objective. Resolve pose, camera, composition, and product presentation in service of that objective.

When a complete line drawing is present, treat its composition as the already-selected shot design. Do not independently redesign the pose, camera, crop, subject scale, support geometry, or major object placement. Describe only the few visible relationships that are genuinely ambiguous or essential to shoe readability.

- Match lens character to the shot instead of defaulting to wide angle.
- Describe observable camera evidence: direction, height, distance, tilt, crop, and foreground-to-background relationships.
- Describe pose geometry: body direction, balance or weight support, hand placement, leg paths, and where each foot lands.
- Use frame-relative terms such as `画面左侧` and `画面右侧` when anatomical left/right could be ambiguous. Give each leg and shoe one stable role.
- Prefer positive spatial instructions over prohibition lists.
- Derive collision and occlusion relationships only from structures visible in the designated references. When exact overlap is unnecessary, prefer clearly separated, photographically plausible silhouettes; never import scene-specific geometry from an unrelated example.
- Keep both shoes separately readable when both matter, and protect the complete contour of a close foreground hero shoe.
- Require credible anatomy, scale, foot contact, and contact shadows.
- Do not invent handheld props. Hands may use natural empty-hand gestures or interact plausibly with supports already visible in the reference.

Do not stack incompatible demands merely for novelty. When requirements compete, state the winning priority and simplify the weaker requirement.

## Resolve aspect ratio

Follow the user's requested ratio and orientation. Otherwise, in line-art-guided recomposition preserve the complete line drawing's ratio and orientation; in single-reference work preserve the color original's. Choose a new ratio by intended use only when neither is available.

## Construct the prompt

Write in the user's language; default to concise natural Chinese when their preference is unclear. Include only the semantic components the shot needs:

- a concise reference anchor;
- the hero objective;
- visible pose geometry;
- camera and composition evidence;
- a few decisive acceptance criteria.

These are content checks, not mandatory headings or a requirement to produce six separate paragraphs. A concise anchor can be adapted from:

> 基于彩色原始参考图创建同一拍摄系列中的一张新照片；除下文明确要求的变化外，保持人物身份、鞋款、造型、场景身份、光线、色调与摄影质感一致。

When a complete line drawing is present, the anchor must identify which image is the color content reference and which is the black-and-white spatial composition reference. State that the same color scene is reconstructed under the line drawing's target camera and layout, not frozen in its old coordinates. The final must be a photorealistic advertising image rather than a colored drawing. Do not send a role sentence, correction fragment, or replacement paragraph by itself; incorporate it into the complete prompt.

State ranked priorities only when the model must resolve genuine competition.

## Adapt for the target model

Keep both versions aligned to the same creative objective and required composition; adapt instruction density rather than inventing different concepts.

### Nano Banana 2

Target Gemini 3.1 Flash Image. Be specific, direct, and compact. State each constraint once, replace abstract spatial language with visible evidence, and retain only details that change the rendered decision.

Reasoning level is an execution setting, not a reason to lengthen the prompt. When relevant, use only the official levels `minimal` and `high`; `minimal` is the default and still performs some thinking.

### Nano Banana Pro

Target Gemini 3 Pro Image. Start from the same concise core, then add precision only for genuinely ambiguous spatial paths, occlusion, product fidelity, camera behavior, or tradeoff priorities. Do not make the Pro prompt long by default or enumerate details already defined clearly by the reference.

## Second-pass prompt check

Before returning prompts, silently reread and revise them once. Confirm that:

- the requested number of shots and prompt blocks is correct;
- each shot has one dominant objective and no repeated constraints;
- every supplied image has the correct explicit role in every complete prompt;
- a complete line drawing controls spatial composition while the color original controls content and appearance;
- the prompt does not simultaneously preserve the color original's old camera or background coordinates;
- any added geometry description resolves a visible ambiguity rather than redundantly narrating the entire line drawing;
- pose instructions use visible geometry and keep shoe roles stable;
- pose, scene structures, camera, crop, anatomy, and product requirements do not conflict;
- the final rendering is explicitly photographic, with no line-art style leakage;
- Nano Banana 2 contains only decisive instructions;
- Nano Banana Pro adds only detail that changes a model decision.

Fix every detected issue before output.

## Output

- **Single shot:** return `Nano Banana 2` and `Nano Banana Pro`, each with a short shot title and one copy-ready code block, unless the user requests one model.
- **Shot set:** number the shots and return the requested model version or versions for each. State the total clearly when one shot produces two prompt blocks.
- **Diagnosis:** briefly return `达成之处`, `主要偏差`, and `重新生成提示词`; the final section contains fresh Nano Banana 2 and Nano Banana Pro prompts unless the user requests one model.

Do not add a separate negative prompt unless requested.
