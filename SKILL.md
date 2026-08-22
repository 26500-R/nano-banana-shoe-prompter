---
name: nano-banana-shoe-prompter
description: Route footwear-model reference requests, offer selectable pose concepts when requested, and write copy-ready Nano Banana / Gemini image prompts, including recomposition from a complete line drawing plus a color original. Use for a new shoe-fashion shot, a coordinated shot set, line-art-guided recomposition, or result diagnosis. Preserve the referenced person, footwear product, outfit, and shoot continuity; never retry from an AI-generated final image.
---

# Nano Banana Shoe Prompter

Write prompts; do not generate images unless the user separately asks for image generation.

## Route the request

Inspect the references first and route by their semantic roles, not attachment count:

- **Content-reference route:** use when the user supplies one or more color photographs but no complete composition drawing. When constructing a full prompt, design the camera, pose, composition, and product presentation explicitly because no separate asset already fixes them.
- **Complete-line-art route:** use only when the user supplies both a complete black-and-white composition drawing and a color original. Read [references/pose-reference.md](references/pose-reference.md); its four-layer prompt structure replaces, rather than supplements, the generic instructions to describe camera, pose, and composition below. Do not transcribe spatial relationships already clear in the drawing.
- **Incomplete-sketch route:** a skeleton, body-only sketch, or drawing without the target frame and support layout does not trigger the complete-line-art route. Use it only as partial guidance, disclose what it cannot control, and describe the missing decisions explicitly.

Then choose the deliverable:

- **Ambiguous image intent:** when the user supplies exactly one unexplained image, do not infer whether it is a color original, generated result, line drawing, or product-only reference from appearance alone. Ask one concise numbered question in the user's language. In Chinese use: `这张图准备怎么使用？1. 这是包含模特与鞋履的彩色原图，先给 10 个简短动作方案；2. 这是彩色人物原图，直接生成完整 Nano Banana 2 提示词；3. 这是 AI 结果图，请诊断；4. 这是线稿或姿势参考，需要配合彩色原图；5. 这是单独鞋款或产品图，需要与人物原图组合使用。` Ask the user to reply with a number. With multiple images, route directly when their roles and requested deliverable are clear; a complete line drawing plus a color original is sufficient to proceed with a complete Nano Banana 2 prompt. If multiple-image roles or the deliverable remain decision-critical and unclear, ask one concise question for only the missing information. Never repeat a question the user's text already answers.
- **Single-image pose discovery:** after the user explicitly requests pose exploration or chooses option 1, read [references/pose-system.md](references/pose-system.md) and return a menu of 10 brief action concepts. Do not write generation prompts yet.
- **Selected-concept expansion:** when the user replies with one or more numbers from that menu, treat each selected concept as a fixed shot brief and expand only those concepts into complete standalone prompts using the same original reference. Preserve its defining body action, support state, leg arrangement, and footwear objective rather than redesigning or loosely reinterpreting it. If the requested number is unavailable or ambiguous, ask one concise question.
- **Single shot:** design one composition with one dominant visual objective.
- **Shot set:** design meaningfully different but visually coherent compositions.
- **Result diagnosis:** compare the result with the designated original assets and intended objective, then correct the instruction rather than the failed pixels.

Treat a **shot, pose, or concept** as one composition and a **prompt** as one copy-ready text block. A brief numbered action concept is not yet a prompt. Complete prompts default to Nano Banana 2; follow an explicit request for Pro or both versions. Respect a user-specified total number of prompts literally.

If a reference-dependent request has no accessible image, ask the user to attach it. Before writing a full prompt, confirm that the designated original assets contain the person, footwear, and other identity the user expects to preserve; request only the missing source instead of inventing it or substituting a generated result. Inspect every supplied reference and result image visually before writing.

- Read [references/prompt-patterns.md](references/prompt-patterns.md) in the content-reference route only when concrete camera, crop, or shot-family guidance is needed.
- Read [references/pose-system.md](references/pose-system.md) after the user chooses the pose-discovery route and whenever they request pose exploration, multiple poses, or body-structure diversity in a shot set.
- Read [references/diagnosis.md](references/diagnosis.md) when evaluating a generated result, visible reasoning, thought images, prompt-length tests, or reasoning settings.

## Generation invariants

Every attempt must use the user-designated original reference assets. Treat AI-generated final advertising images only as diagnostic evidence and never recommend them as source images for another generation, including minor corrections; repeated editing can accumulate quality loss, lost detail, and color drift.

Every delivered prompt must be complete, standalone, and usable with all designated original assets without relying on a previous prompt or result. `Standalone` means directly usable together with those assets; it does not mean the prompt must reproduce their visible content in words or work without them. Honor the user's image labels and semantic roles; do not silently reassign them by upload order. Treat interface-generated ordinals such as `Image #1` as labels only if the user adopts them. When the user supplies labels, pair each label with its semantic role once, then use that label consistently.

Unless the user requests a change, preserve the designated person's identity, exact footwear, outfit, scene identity, and photographic appearance. Preserve worn, carried, held, or otherwise used accessories and props when their relationship to the subject matters. The color original is authoritative for what every retained person, product, object, and scene element is and how it looks, but incidental background items do not all have to appear in a new composition. In the complete-line-art route, express this authority once through the route's reference-role layer rather than repeatedly restating content details. Infer only what the references support; do not invent hidden product construction, logos, accessories, furniture, or scene features.

Anchor preserved content to the references instead of transcribing it as a checklist. Name a visible detail only when it resolves a real ambiguity or changes a rendering decision. When several candidate products are present, identify which one is the hero product without enumerating its visible parts merely to prove recognition. Do not quote attachment filenames unless multiple references of the same type would otherwise be ambiguous. Never mention future face swapping, shoe replacement, inpainting, local repair, or downstream post-production in a generation prompt.

Treat overlaid captions, page graphics, and watermarks as layout rather than physical scene content. Include a nonphysical overlay only when the user requests it or a designated composition reference intentionally contains it. When an unwanted overlay is visibly likely to transfer, add one concise positive clean-photography instruction following [references/prompt-patterns.md](references/prompt-patterns.md); otherwise omit it rather than adding a prohibition list. Preserve genuine product branding and physical signage when visible.

## Design the shot

Use this section to supply spatial decisions in the content-reference and incomplete-sketch routes. In the complete-line-art route, the drawing already supplies those decisions; follow [references/pose-reference.md](references/pose-reference.md) and describe only unresolved ambiguity or a decision critical to shoe readability.

Give each shot one hero objective. Resolve pose, camera, composition, and product presentation in service of that objective.

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

Follow the user's requested ratio and orientation. In the complete-line-art route, when the user has not specified a numeric ratio, preserve the drawing's original ratio and orientation but refer to them relationally in the prompt, such as `保持图1原始画幅比例和方向`; do not infer or write a numeric ratio. In other routes, preserve the designated composition reference's ratio and orientation, or the original's in single-reference work. Choose a new ratio by intended use only when no controlling reference is available.

## Construct the prompt

The component checks in this section apply directly to the content-reference and incomplete-sketch routes. In the complete-line-art route, use the four required layers in [references/pose-reference.md](references/pose-reference.md); the drawing replaces pose or camera prose already visible in it, while reconstruction and anti-line-art constraints remain explicit.

Write in the user's language; default to clear natural Chinese when their preference is unclear. Include the semantic components the shot needs:

- a reference anchor;
- the hero objective;
- visible pose geometry;
- camera and composition evidence;
- decisive acceptance criteria.

These are content checks, not mandatory headings or a required paragraph count. Use one reference anchor to identify the designated original assets and state that unrequested content remains consistent. Enumerate preserved domains only when their roles would otherwise be ambiguous.

State ranked priorities only when the model must resolve genuine competition.

## Adapt for the target model

When both model versions are explicitly requested, keep them aligned to the same creative objective and required composition; adapt instruction density rather than inventing different concepts. Prompt length is a consequence of the decisions that must be expressed, not a target or a quality measure. Remove repeated or non-decision-changing text, but never remove a needed constraint merely to make the prompt shorter.

### Nano Banana 2

Target Gemini 3.1 Flash Image. Be specific, direct, and compact: state each constraint once, replace abstract spatial language with visible evidence, and remove only repetition or detail that does not change the rendered decision. Here `compact` means non-redundant, not short; use as many sentences or paragraphs as the actual ambiguity, support, occlusion, products, references, or layout decisions require.

### Nano Banana Pro

Target Gemini 3 Pro Image. Start from the same complete, non-redundant core, then add precision only for genuinely ambiguous spatial paths, occlusion, product fidelity, camera behavior, or tradeoff priorities. Do not add detail merely to distinguish Pro from Nano Banana 2 or enumerate content already defined clearly by the references. When the references leave no material decision unresolved, the Pro prompt may retain the same concise core without forced expansion.

## Second-pass prompt check

Before returning prompts, silently reread and revise them once. Confirm that:

- the reference route is correct and route-specific rules were not stacked together;
- the requested number of shots and prompt blocks is correct;
- an unexplained single image receives the intent question instead of an assumed route, while clear single- or multiple-image roles are not interrupted by a redundant question;
- a pose-discovery response contains concepts rather than premature prompt blocks, and no Pro prompt appears unless explicitly requested;
- every prompt is complete, standalone, and assigns supplied references correctly;
- each shot has one dominant objective, and its pose, scene, camera, anatomy, and product requirements are compatible;
- Nano Banana 2 contains only decisive instructions, while Nano Banana Pro adds only detail that changes a model decision;
- no sentence restates a reference role, repeats a constraint with synonyms, or inventories content already clear in a designated reference.

Fix every detected issue before output.

## Output

- **Ambiguous image intent:** return only the concise route question above. Inspect the image internally as needed, but do not present image analysis, concepts, or prompts yet.
- **Single-image pose discovery:** return exactly 10 numbered, easy-to-imagine action concepts following [references/pose-system.md](references/pose-system.md), then ask the user to reply with one or more numbers. Do not include code blocks or full prompts.
- **Selected-concept expansion or direct single shot:** return one complete prompt per selected shot, each with a short title and one copy-ready code block. Default to Nano Banana 2 and follow any explicit request for Pro or both versions.
- **Shot set:** number the shots and return the explicitly requested model version or versions for each; default to Nano Banana 2 only.
- **Diagnosis:** follow the conditional output headings in [references/diagnosis.md](references/diagnosis.md); write a retry prompt only when the designated original assets are available.

Do not add a separate negative prompt unless requested.
