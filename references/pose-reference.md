# Complete Line-Art Composition Reference

Use this file when the user supplies both a color footwear-model original and a complete black-and-white line drawing intended to control the new shot. This is a whole-composition workflow, not generic pose-only transfer: the line drawing supplies the target two-dimensional spatial template, while the color original supplies the authoritative content inventory and photographic appearance rebuilt inside it.

## 1. Confirm that the line drawing is complete enough

A suitable composition line drawing normally shows:

- the target frame and crop;
- the person's visible placement, scale, body outline, pose, and principal occlusion order;
- both required feet or shoes and their frame locations;
- support surfaces and contact relationships;
- the positions or silhouettes of major props and scene structures that affect composition.

It does not need high image quality, realistic texture, identity, color, or product detail. Because it may be AI-generated, treat its outlines only as spatial evidence; determine what actually exists and how it looks from the color original. Sparse joint skeletons, isolated anatomy diagrams, and body-only sketches without the target frame or support layout are not equivalent to this workflow. If the drawing is incomplete, disclose the missing spatial control and do not promise exact composition transfer.

## 2. Assign the two semantic roles once

Honor the user's labels and state these roles once inside every standalone prompt; do not rely on upload order. Use one domain-level role sentence rather than expanding either role into a list. With user-adopted labels `图1` and `图2`, prefer this exact shape:

`图1是完整黑白构图线稿，只控制目标空间构图；图2是彩色原始参考图，控制所有真实内容与摄影观感；在图1的布局中重建图2。`

- The **complete black-and-white line drawing** controls target ratio when the user has not specified another, frame, crop, observable camera and perspective cues, subject placement and scale, pose, occlusion, support relationships, shoe locations, and the spatial layout it actually depicts.
- The **color original** is the authoritative source for every actual person, footwear product, garment, accessory, prop, scene object, design, material, color, light, and photographic characteristic.
- The line drawing is not a content inventory: an omission does not remove content supported by the color original, and an extra or inaccurate outline does not authorize new content or override the color original's design.

A line drawing produced by a separate pose-transfer process is an original spatial-control asset for this workflow, not an AI-generated final advertisement or a replacement content source.

## 3. Reconstruct rather than freeze the color original

Rebuild the color original's scene identity and recognizable content under the line drawing's camera, perspective, crop, support geometry, and object placement. Do not simultaneously preserve the color original's old camera, pose, crop, background perspective, or object coordinates.

When requirements conflict, use this order:

1. the user's explicit request;
2. the line drawing for spatial geometry;
3. the color original for content identity and photographic appearance.

This order separates responsibilities; it does not make an AI-generated line drawing a higher-fidelity content source than the color original.

If a major drawn object has no supported counterpart in the color original and the user did not request a new object, the drawing may define only its occupancy or support relationship, not its identity or design. Conversely, preserve content from the color original even when the drawing omits it, adapting its placement to the target composition while retaining its supported use relationship, such as worn, carried, held, or placed. If an object's identity or placement remains decision-critical and genuinely unresolved, disclose the ambiguity instead of inventing it. Do not silently import unrelated furniture, products, clothing, or props from the workflow that produced the drawing.

## 4. Build a non-redundant, sufficient prompt

Open every complete-line-art prompt with one winning-priority sentence. With user-adopted label `图1`, prefer this exact shape and fill only the requested format and output type:

`严格遵循图1提供的完整黑白构图线稿来精确确定空间构图和物体位置，不作自由变化或创造性偏移，生成一张[画幅与成片类型]。`

Do not insert a list of camera, crop, pose, support, occlusion, shoe, or scene relationships into this sentence; the drawing already expresses them.

The default prompt shape is the priority sentence above plus the single short role sentence from section 2. If the opening already names the output type, do not add another generic output or quality sentence. Add further text only when you can name a concrete unresolved decision, the user explicitly requests the constraint, or a diagnosed result has failed on that point; never use an extra sentence to restate either reference role or the opening priority. Treat anatomy, support, contact, shoe contours, line-art leakage, old color-original coordinates, and nonphysical overlays as silent reasoning and final checks. Do not inventory visible content from the color original or convert the complete drawing into prose merely to demonstrate that the references were inspected.

This is a role-and-decision structure, not a compression pattern or length target. Include every decision-changing constraint required by an ambiguous or incomplete drawing, complex support or occlusion, multiple references or products, or exact text and layout requirements. Remove repeated meaning, but never delete a needed spatial or product constraint merely to reduce length.

Do not narrate joints, background edges, garments, accessories, scene objects, materials, shoe components, camera, pose, or layout evidence already clear in the designated references. A broad category list is still an inventory even when each item appears only once. Do not describe the task as coloring, tracing, converting, or editing the drawing. Avoid repeated intensifiers such as `唯一来源`, `严格`, `完全相同`, and `必须` after the opening priority has resolved the issue.

Apply the global model-density rules. In this workflow, extra Pro detail is justified only when it resolves uncertain occlusion, support, perspective, product fidelity, or scene reconstruction. The fact that footwear is the hero product does not by itself justify restating generic shoe-contour, anatomy, support, contact, or shadow requirements. Before returning, confirm silently that the prompt does not preserve the color original's old coordinates or inherit black lines, sketch shading, paper texture, or illustration treatment from the drawing.

Treat improved adherence observed with complete line drawings as tested workflow experience, not official Google guidance and not a guarantee for every image or model version.
