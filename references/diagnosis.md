# Result Diagnosis

Use this when the user supplies a generated result, visible reasoning, thought images, or a controlled prompt/model comparison. Apply the generation invariants to every retry; in a line-art-guided shot, diagnose against the color original and the same complete black-and-white line drawing, treating the generated final image only as evidence.

If the user supplies the real photo from which an AI line drawing was derived, use it only to validate spatial adherence unless the user also designates it as a generation content source. Do not count content differences required by the actual color source as failures.

## Diagnose by impact

Evaluate in this order:

1. **Product fidelity and readability:** shoe design, proportions, materials, branding, complete contours, focus, and commercial usefulness.
2. **Identity and continuity:** person, hairstyle, body characteristics, outfit, accessories, props, scene objects, lighting, and color treatment.
3. **Pose and anatomy:** intended geometry, balance, limb plausibility, hands, foot contact, and contact shadows.
4. **Camera and composition:** viewpoint evidence, perspective, crop, scale, depth layers, and aspect ratio.
5. **Image cleanliness:** duplicate objects, warped geometry, unexplained props, embedded text, or broken background continuity.

Report what succeeded, then only the two or three failures that most undermine the hero objective.

## Use reasoning traces cautiously

Rendered pixels are the evidence. Do not accept a model's claim of full compliance, or its own reported defect, without checking the image.

Trace length does not measure prompt quality or instruction difficulty. When comparing prompt lengths, keep the model, reasoning level, original reference, creative objective, and other available settings the same. A Nano Banana 2 versus Nano Banana Pro comparison cannot isolate prompt length because the model also changed.

Gemini 3.1 Flash Image uses the official reasoning levels `minimal` and `high`; `minimal` is the default and still performs some thinking. Reasoning effort and reasoning visibility are separate variables.

### API-specific visibility

- The legacy `generateContent` API uses `thinkingConfig.includeThoughts` to request thought parts. See Google's [Legacy GenerateContent image guide](https://ai.google.dev/gemini-api/docs/generate-content/image-generation).
- The Interactions API represents reasoning as dedicated `thought` steps. Google's general [Interactions thinking guide](https://ai.google.dev/gemini-api/docs/thinking) uses `generation_config.thinking_summaries` to request summaries, while the current [Interactions image guide](https://ai.google.dev/gemini-api/docs/image-generation) demonstrates reading text and image content from each thought step's `summary`.

Do not describe `includeThoughts` as a universal field or as an Interactions API setting. The two APIs expose reasoning through different response structures.

### Thought images

Current Google documentation says Gemini 3 image models can generate up to two interim images to test composition and logic, and that the last image within Thinking is the final rendered image in the Interactions API. A product interface may expose only part of this sequence, so record only what is visible and do not infer unseen synthesis steps or pixel reuse.

Use visible traces for three signals:

- **Objective drift:** the trace or images change the frame-relative hero shoe or foreground/midground assignment. Rewrite with one stable assignment.
- **Instruction absorption:** the trace restates the requested geometry but the pixels still fail. Simplify the pose or fragile occlusion instead of adding synonyms.
- **False self-assessment:** the model claims compliance that the image does not show. Base the diagnosis on the rendered result.

When prompts produce comparable fidelity, prefer the version with less repeated or non-decision-changing text, not the one with fewer characters. Keep extra Pro detail only if it changes a concrete spatial, product, camera, or priority decision.

## Map drift to a correction

| Drift | Likely cause | Better correction |
|---|---|---|
| Shoe design changed | Product fidelity competed with unnecessary description | Anchor the exact footwear to the original reference and remove decorative product adjectives |
| Face or body changed | Identity was omitted or overwhelmed by a large transformation | Lock the same recognizable person and simplify other changes |
| Foreground shoe cropped | Camera proximity lacked contour protection | Keep the complete hero shoe inside frame with room around toe, heel, and sole |
| Shoes merge or overlap | Foot positions were vague | Assign each foot a separate frame region and depth role |
| Floating or twisted foot | Support geometry was underspecified | Name the landing surface, ankle orientation, and contact shadow |
| Perspective is too weak | Only a focal-length label was given | Add visible viewpoint and foreground-to-background scale evidence |
| Distortion is excessive | Wide lens, close distance, and proportion accuracy competed | Move the camera back or use milder lens character |
| Scene drifted | The prompt redescribed or embellished the environment | Anchor the scene and remove invented décor, materials, or lighting |
| Pose ignored | Too many objectives competed | Keep one hero objective and retain only decision-changing pose geometry |
| Color-source content was omitted, redesigned, or repurposed | The line drawing was treated as a content inventory | Restore the content and supported use relationship from the color original, then adapt its placement within the target spatial composition |
| Complete line drawing ignored | The prompt treated it as pose-only or also froze the color original's old composition | Assign the line drawing full spatial authority and reconstruct the color scene within it |
| Output looks illustrated | Line-art style leaked into the rendering objective | State that the line drawing is only a spatial template and request a new photorealistic image |
| Unwanted text remains | Overlay removal was ambiguous | Request a pure photographic frame and continuous replacement texture |

## Output

Use three compact parts:

1. **达成之处** — only elements worth retaining.
2. **主要偏差** — prioritized visible failures and likely instruction causes.
3. **重新生成提示词** — by default, one fresh Nano Banana 2 prompt and one fresh Nano Banana Pro prompt following the global generation invariants; return one only when the user requests a single model.
