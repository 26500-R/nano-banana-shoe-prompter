# Complete Line-Art Composition Reference

Use this file when the user supplies both a color footwear-model original and a complete black-and-white line drawing intended to control the new shot. This is a whole-composition workflow, not generic pose-only transfer: the line drawing supplies the target two-dimensional spatial template, while the color original supplies the authoritative content identity and photographic appearance rebuilt inside it.

## 1. Confirm that the line drawing is complete enough

A suitable composition line drawing normally shows:

- the target frame and crop;
- the person's visible placement, scale, body outline, pose, and principal occlusion order;
- both required feet or shoes and their frame locations;
- support surfaces and contact relationships;
- the positions or silhouettes of major props and scene structures that affect composition.

It does not need high image quality, realistic texture, identity, color, or product detail. Because it may be AI-generated, treat its outlines only as spatial evidence; determine what actually exists and how it looks from the color original. Sparse joint skeletons, isolated anatomy diagrams, and body-only sketches without the target frame or support layout are not equivalent to this workflow. If the drawing is incomplete, disclose the missing spatial control and do not promise exact composition transfer.

## 2. Assign the two semantic roles once

Honor the user's labels and state these roles once inside every standalone prompt; do not rely on upload order. Use one domain-level role paragraph and do not repeat its domains elsewhere. With user-adopted labels `图1` and `图2`, prefer this shape:

`图1是完整黑白构图线稿，负责最终画面的空间构图、机位、人物位置与尺度、姿势、遮挡、支撑关系、双鞋位置和主要物体布局；图2是彩色原始参考图，负责所有真实人物、鞋履产品、服装配饰、场景内容、材质颜色、光线和摄影质感。`

- The **complete black-and-white line drawing** controls target ratio when the user has not specified another, frame, crop, observable camera and perspective cues, subject placement and scale, pose, occlusion, support relationships, shoe locations, and the spatial layout it actually depicts.
- The **color original** is the authoritative source for what every retained person, footwear product, garment, accessory, prop, scene object, design, material, color, light, and photographic characteristic is and how it looks. This source authority does not require every incidental background item to appear in the new frame.
- The line drawing is not a content inventory: an omission does not remove the person, footwear, outfit, or a worn, carried, held, or otherwise important item supported by the color original, and an extra or inaccurate outline does not authorize new content or override the color original's design.

A line drawing produced by a separate pose-transfer process is an original spatial-control asset for this workflow, not an AI-generated final advertisement or a replacement content source.

## 3. Reconstruct rather than freeze the color original

Rebuild the color original's scene identity and recognizable content under the line drawing's camera, perspective, crop, support geometry, and object placement. Do not simultaneously preserve the color original's old camera, pose, crop, background perspective, or object coordinates.

When requirements conflict, use this order:

1. the user's explicit request;
2. the line drawing for spatial geometry;
3. the color original for content identity and photographic appearance.

This order separates responsibilities; it does not make an AI-generated line drawing a higher-fidelity content source than the color original.

If a major drawn object has no supported counterpart in the color original and the user did not request a new object, the drawing may define only its occupancy or support relationship, not its identity or design. Preserve the person, footwear, outfit, and content with an important ownership or use relationship from the color original even when the drawing omits it, adapting placement to the target composition. Incidental background items need not be forced into the new frame. If an object's identity or placement remains decision-critical and genuinely unresolved, disclose the ambiguity instead of inventing it. Do not silently import unrelated furniture, products, clothing, or props from the workflow that produced the drawing.

## 4. Build a non-redundant, sufficient prompt

Open every complete-line-art prompt with one winning-priority sentence. With user-adopted label `图1`, use the user's explicit ratio when supplied; otherwise refer to the drawing's ratio and direction without guessing a numeric value. Prefer these exact shapes and fill only the output type:

- Explicit ratio: `严格遵循图1提供的完整黑白构图线稿来精确确定空间构图和物体位置，不作自由变化或创造性偏移，生成一张[用户指定画幅与成片类型]。`
- No explicit ratio: `严格遵循图1提供的完整黑白构图线稿来精确确定空间构图和物体位置，不作自由变化或创造性偏移，生成一张保持图1原始画幅比例和方向的[成片类型]。`

Do not insert a list of camera, crop, pose, support, occlusion, shoe, or scene relationships into this sentence; the drawing already expresses them.

Use four necessary layers in every complete-line-art prompt:

1. **Spatial priority:** the opening sentence above.
2. **Reference roles:** the single role paragraph from section 2.
3. **Reconstruction rather than overlay:** state once that the color original is rebuilt inside the drawing's complete composition without retaining or superimposing its old camera, pose, limb positions, or object coordinates. Recreate only the people, limbs, footwear, and objects actually supported by the color original, in their supported ownership and use relationships, so old and target arrangements are not combined.
4. **Unified photographic output:** in Chinese prompts, use this fixed sentence exactly: `按图1的构图，以图2的真实摄影质感重建成片，不保留任何线稿或插画效果。` Use a faithful semantic equivalent in another output language. Do not expand it into another list of line-art artifacts.

These layers prevent different failure modes and are not removable merely because the prompt could be shorter. State each layer once, without synonyms or a second inventory. Add further text only when a concrete ambiguity, explicit user request, complex support or occlusion, multiple products, exact layout, or diagnosed failure requires another decision. Do not convert the complete drawing or color original into a visual checklist merely to demonstrate that the references were inspected.

This is a role-and-decision structure, not a compression pattern or length target. Include every decision-changing constraint required by an ambiguous or incomplete drawing, complex support or occlusion, multiple references or products, or exact text and layout requirements. Remove repeated meaning, but never delete a needed spatial or product constraint merely to reduce length.

Do not narrate joints, background edges, individual garment details, individual accessories, scene-object appearances, material details, shoe components, camera, pose, or layout evidence already clear in the designated references. The domain list in the single reference-role paragraph is sufficient; do not expand it into itemized visual descriptions. Do not describe the task as coloring, tracing, converting, or editing the drawing. Avoid repeated intensifiers such as `唯一来源`, `严格`, `完全相同`, and `必须` after the opening priority has resolved the issue.

Apply the global model-density rules. When both model versions are explicitly requested, both retain all four layers. Extra Pro detail is justified only when it resolves uncertain occlusion, support, perspective, product fidelity, or scene reconstruction; the fact that footwear is the hero product does not by itself justify restating generic shoe-contour, anatomy, support, contact, or shadow requirements.

Treat improved adherence observed with complete line drawings as tested workflow experience, not official Google guidance and not a guarantee for every image or model version.
