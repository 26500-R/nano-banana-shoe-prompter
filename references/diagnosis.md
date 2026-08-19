# Result Diagnosis

Use this only when the user supplies both an original reference and a generated result, or clearly describes a failed result. Treat the generated result as diagnostic evidence only, never as the source image for another generation.

## Diagnose by impact

Evaluate in this order:

1. **Product fidelity:** shoe category, silhouette, materials, color blocking, sole, closures, proportions, and visible branding.
2. **Identity and continuity:** same recognizable person, hairstyle, body characteristics, outfit, scene, furniture, lighting, and color treatment.
3. **Product readability:** complete contours, independent visibility, important product surfaces, occlusion, focus, and commercial usefulness.
4. **Pose and anatomy:** intended geometry, balance, limb plausibility, hands, foot-ground contact, and believable contact shadows.
5. **Camera and composition:** viewpoint evidence, perspective strength, crop, scale, depth layers, and aspect ratio.
6. **Image cleanliness:** duplicate objects, warped geometry, unexplained props, embedded text, or broken background continuity.

Do not produce a long checklist. Report what succeeded, then the two or three failures that most undermine the hero objective.

## Use model reasoning cautiously

If the user provides the image model's visible reasoning or progress text, use it only as a diagnostic trace and compare it with the rendered pixels. Do not accept statements such as “fully compliant” or “precisely matched” as evidence.

Do not infer prompt quality, prompt length, or instruction difficulty from the length of that trace. A concise prompt can produce longer or more repetitive progress narration than a detailed prompt; judge efficiency by the rendered result and constraint compliance.

Treat reasoning effort and reasoning visibility as separate variables. If a product surface hides the trace at a particular setting, record the trace as unavailable; do not infer that the model skipped reasoning or edited the image directly. When comparing prompts, keep the reasoning level the same. When comparing reasoning levels, keep the model, prompt, original reference, and other available generation settings the same.

### Intra-request thought images

Google's [official image-generation guide](https://ai.google.dev/gemini-api/docs/image-generation) says Gemini 3 image thinking can generate interim **thought images** to refine composition before the final output. If an image appears during visible reasoning and is followed by a different returned image, record it as an intra-request thought image, not as evidence of user-initiated multi-turn editing. The documentation does not specify whether later image synthesis reuses earlier thought-image pixels, so do not claim either fresh resampling or pixel editing.

The official API exposes only `minimal` and `high` for Gemini 3.1 Flash Image; `minimal` is the default and does not mean thinking is off. The user's translation plugin renders `minimal` as `中`; record those runs as `minimal`, never as `medium`. Thought visibility can be controlled separately with `includeThoughts`, so a hidden trace is not evidence that no thinking or thought images occurred. Evaluate every visible thought image and the returned image independently. Do not assume the last image is best: internal self-critique can reject a stronger candidate or reverse a correct foreground/background assignment.

Look for three useful signals:

- **Objective drift:** the trace alternates between focal shoes or changes foreground/midground assignments. Before calling this drift, determine whether the trace switched from frame-relative terms to the subject's anatomical left/right; use the rendered positions as the deciding evidence. If the rendered role truly changed, rewrite the prompt with one frame-relative hero shoe and one stable placement for the other shoe.
- **Instruction absorption:** the trace restates concrete positions correctly but the image still fails. Treat this as a geometry-generation limit rather than adding more synonymous wording; simplify the pose or remove a fragile occlusion.
- **False self-assessment:** the trace or accompanying text may claim exact compliance despite visible failures, or report a defect that the rendered image does not contain. Base both praise and criticism on the image, not the model's claim.

When detailed and concise prompts produce comparable fidelity, prefer the concise version. Keep extra Pro detail only if it changes a concrete spatial, product, camera, or priority decision.

For a prompt-length comparison, keep the target model, reasoning level, original reference, creative objective, and available generation settings the same. A Nano Banana 2 versus Nano Banana Pro comparison cannot isolate the effect of prompt length because the model also changed.

## Find the likely instruction failure

Map visible drift to a prompt correction:

| Drift | Likely cause | Better correction |
|---|---|---|
| Shoe design changed | Product was summarized too loosely or competed with styling requests | Anchor the exact footwear to the original reference and remove unnecessary product adjectives |
| Face or body changed | Identity was omitted or overwhelmed by a large pose/style change | Explicitly lock the same recognizable person and simplify other transformations |
| Foreground shoe cropped | Camera proximity was specified without contour protection | Require the complete hero shoe inside frame with breathing room around toe, heel, and sole |
| Shoes merge or overlap | Foot positions were vague | Assign each foot a separate frame region and state foreground/midground placement |
| Floating or twisted foot | Pose geometry and support were underspecified | Name the weight-bearing leg, landing surface, ankle orientation, and contact shadow |
| Perspective is too weak | Only a focal length label was given | Add observable low/high viewpoint evidence and explicit foreground-to-background scale relationships |
| Distortion is excessive | Wide lens, close distance, and proportion accuracy competed | Relax one variable; move the camera back or use a milder lens character |
| Scene drifted | The prompt redescribed or embellished the environment | Anchor the existing scene and remove invented décor, materials, or lighting |
| Pose ignored | Too many hero objectives competed | Keep one hero objective and make the pose geometry shorter and more explicit |
| Unwanted text remains | The request treated overlays ambiguously | Ask for a pure photographic frame and continuous background texture in the covered regions |

## Output structure

Use three compact parts:

1. **达成之处** — only the elements worth retaining.
2. **主要偏差** — prioritized observable failures and their likely prompt cause.
3. **重新生成提示词** — one fresh, complete, self-contained prompt to submit with the original reference. Do not return only correction clauses or a partial prompt.

Correct the instruction, not the failed pixels. Never recommend or perform another edit pass on an AI-generated result. Every new attempt must start from the original reference image to avoid cumulative quality loss, detail loss, and color drift.
