# Complete Line-Art Composition Reference

Use this file when the user supplies both a color footwear-model original and a complete black-and-white line drawing intended to control the new shot. This is a whole-composition workflow, not generic pose-only transfer: the line drawing supplies the target two-dimensional spatial template, while the color original supplies the content and photographic appearance rebuilt inside it.

## 1. Confirm that the line drawing is complete enough

A suitable composition line drawing normally shows:

- the target frame and crop;
- the person's visible placement, scale, body outline, pose, and principal occlusion order;
- both required feet or shoes and their frame locations;
- support surfaces and contact relationships;
- the positions or silhouettes of major props and scene structures that affect composition.

It does not need high image quality, realistic texture, identity, color, or product detail. Sparse joint skeletons, isolated anatomy diagrams, and body-only sketches without the target frame or support layout are not equivalent to this workflow. If the drawing is incomplete, disclose the missing spatial control and do not promise exact composition transfer.

## 2. Assign the two semantic roles once

Honor the user's labels and state these roles once inside every standalone prompt; do not rely on upload order.

- The **complete black-and-white line drawing** controls target ratio when the user has not specified another, frame, crop, observable camera geometry, subject placement and scale, pose, occlusion, support relationships, shoe locations, and the spatial layout of major drawn scene elements.
- The **color original** is the source for the recognizable person, body and face, hair, exact footwear, outfit, accessories, scene identity, materials, colors, lighting, and photographic character.
- The line drawing never supplies identity, product or garment design, brand detail, material, color, or illustration style, even when its outlines resemble those things.

A line drawing produced by a separate pose-transfer process is an original spatial-control asset for this workflow, not an AI-generated final advertisement or a replacement content source.

## 3. Reconstruct rather than freeze the color original

Rebuild the color original's scene identity and recognizable content under the line drawing's camera, perspective, crop, support geometry, and object placement. Do not simultaneously preserve the color original's old camera, pose, crop, background perspective, or object coordinates.

When requirements conflict, use this order:

1. the user's explicit request;
2. the line drawing for spatial geometry;
3. the color original for content identity and photographic appearance.

If a major drawn object has no supported counterpart in the color original and the user did not request a new object, treat it only as a neutral occupancy or support shape when possible. Do not silently import unrelated furniture, products, clothing, or props from the workflow that produced the drawing.

## 4. Build a compact but sufficient prompt

The default prompt shape is:

1. assign the line drawing to spatial composition and the color original to content and photographic appearance;
2. request reconstruction of the same color scene under the line drawing's target camera and layout;
3. describe only relationships that remain genuinely ambiguous or are critical to shoe readability;
4. require a new photorealistic advertising image with plausible anatomy, support, contact, and complete shoe contours, without line-art leakage.

This is a compression pattern, not a sentence or character cap. Expand it whenever decision-changing information is necessary, including an ambiguous or incomplete drawing, complex support or occlusion, multiple references or products, or exact text and layout requirements. Never delete a needed spatial or product constraint merely to keep the prompt short.

Do not narrate every joint, background edge, garment, accessory, scene object, material, or shoe component already clear in the designated references. Do not describe the task as coloring, tracing, converting, or editing the drawing. Avoid repeated intensifiers such as `唯一来源`, `严格`, `完全相同`, and `必须` when the semantic role assignment already resolves the issue. Use stronger wording only for a genuine winning priority.

Nano Banana 2 receives the compact role split plus decisive ambiguity checks. Nano Banana Pro starts from the same core and adds only decisions needed to resolve uncertain occlusion, support, perspective, product fidelity, or scene reconstruction; it is not a full inventory of visible content.

## 5. Check before returning

Confirm that:

- both roles are stated once and the prompt remains independently usable with both references;
- the line drawing controls target space while the color original controls content and appearance, without preserving the color original's old coordinates;
- added prose resolves a real ambiguity rather than narrating the drawing or inventorying the color image;
- anatomy, occlusion, support, perspective, and shoe readability are plausible;
- the requested output is photographic and does not inherit black lines, sketch shading, paper texture, or illustration treatment.

Treat improved adherence observed with complete line drawings as tested workflow experience, not official Google guidance and not a guarantee for every image or model version.
