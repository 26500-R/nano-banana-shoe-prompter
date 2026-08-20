# Complete Line-Art Composition Reference

Use this file when the user supplies both a color footwear-model original and a complete black-and-white line drawing intended to lock the new shot.

This workflow is not a generic pose-only transfer. A complete line drawing acts as a two-dimensional spatial template for the whole shot. The color original supplies the content and photographic appearance that must be rebuilt inside that template.

## 1. Confirm that the line drawing is complete enough

A suitable composition line drawing normally shows:

- the intended target frame and crop;
- the person's full visible placement, scale, body outline, pose, and principal occlusion order;
- both required feet or shoes and their frame locations;
- support surfaces and contact relationships;
- the positions or silhouettes of major props and scene structures that affect composition.

It does not need high image quality, realistic texture, identity, color, or product detail. Sparse joint skeletons, isolated anatomy diagrams, and body-only sketches without the target frame or support layout are not equivalent to this workflow. If the supplied drawing is incomplete, disclose the missing spatial control and do not promise exact composition transfer.

## 2. Assign image roles semantically

Honor the user's labels and keep them in every complete prompt. Do not rely on upload order.

- The **complete black-and-white line drawing** controls target aspect ratio when the user has not specified another, frame, crop, observable camera geometry, subject position and scale, full-body pose, overlap and occlusion, support relationships, shoe locations, and the spatial layout of major drawn scene elements.
- The **color original** is the sole source for the recognizable person, body appearance, face, hair, exact footwear product, outfit, accessories, scene identity, materials, colors, lighting, and photographic character.
- A line drawing never supplies identity, garment design, shoe design, brand detail, material, color, or illustration style, even when its outlines resemble those things.

A line drawing produced by a separate pose-transfer process is a spatial-control asset, not a generated final advertisement and not a replacement content source.

## 3. Reconstruct rather than freeze the original scene

The target camera and pose may require a different spatial relationship from the color original. Preserve the same scene identity and recognizable visual elements, but rebuild them under the line drawing's camera, perspective, crop, and object placement.

Do not ask for both the line drawing's target composition and the color original's old object coordinates, camera, crop, or background perspective. When they conflict:

1. the user's explicit request wins;
2. the line drawing wins for spatial geometry;
3. the color original wins for content identity and visual appearance.

If a major line-drawn object has no supported counterpart in the color original and the user did not request a new object, treat it only as a neutral occupancy or support shape when possible. Do not silently import unrelated furniture, products, clothing, or props from the process that produced the line drawing.

## 4. Write the prompt as role assignment plus decisive checks

The prompt must be complete and independently usable with both references. Its compact core should establish:

- the two semantic image roles;
- photorealistic reconstruction of the color original inside the line drawing's complete composition;
- preservation of the exact person, outfit, footwear, accessories, scene identity, light, color, and photographic character from the color original;
- only the few line relationships that remain visually ambiguous or are critical to shoe readability;
- final checks for anatomy, support contact, complete shoe contours, and photographic rendering.

Do not narrate every joint or background edge already clear in a complete line drawing. Repeating the drawing in long prose can introduce conflicts. Do not describe the result as coloring, tracing, converting, or editing the line drawing; request a new photorealistic advertising image using it as the spatial template.

Nano Banana 2 should receive the concise role split and only decisive ambiguity checks. Nano Banana Pro may add detail only where occlusion, support, perspective, product fidelity, or scene reconstruction remains genuinely uncertain.

## 5. Check before returning

Confirm that:

- every prompt is complete and identifies the color original and complete line drawing by semantic role;
- the line drawing controls spatial composition and the color original controls content and appearance;
- the prompt does not freeze the color original's old camera or scene coordinates;
- no AI-generated final advertising image is used as a retry source;
- a retry uses the same color original and the same line drawing;
- both shoes remain anatomically attached, complete, recognizable, and commercially readable;
- support, contact shadows, occlusion, and perspective agree with the line drawing;
- the final output is photographic and does not inherit black lines, sketch shading, blank-paper texture, or illustration treatment.

Treat improved adherence observed with complete line drawings as tested workflow experience, not official Google guidance and not a guarantee for every image or model version.
