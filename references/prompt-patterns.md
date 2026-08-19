# Prompt Patterns

Use these as decision patterns, not text templates. Anchor preserved details to the original reference and describe the intended change in detail. Every pattern is conditional: apply it only when the current reference contains the required scene structure, and never import geometry or props from another example.

## Shot patterns

### Natural catalog full body

Use a 35–50 mm look. Put weight on one leg and move the other foot slightly forward or outward. Keep both shoe contours separate, show enough floor to verify contact, and favor product proportion accuracy over spectacle.

### Environmental fashion full body

Use a 28–35 mm look. Place the subject within a visible, usable part of the reference environment. Build depth from existing foreground, subject, and background elements instead of inventing furniture or accessories.

### Low-angle shoe hero

Use a deliberate 20–28 mm look. Put one complete shoe in the lower foreground and the other in the midground. State which leg bears weight and how the body recedes through the frame. A seated, half-seated, stepping, crouched, or extended-leg pose generally handles this perspective better than rigid standing.

Suggested priority language:

> 最终画面依次优先保证鞋款与参考图一致、前景主鞋完整清晰、低机位空间纵深成立，以及人物姿态自然可信。

### High-angle full body

Describe evidence rather than only naming the angle: camera above the head, visible top of head and shoulders, visible shoe uppers, compressed body depth, and substantial floor around the subject. Use 28–35 mm for a natural result or 20–28 mm for intentional exaggeration.

### Seated shoe presentation

Use only a seat visible in the reference. Specify pelvis placement, torso direction, which leg extends, where the other foot lands, and how the two shoes occupy separate frame regions. Keep hands empty unless an existing prop interaction supports the shot.

Conditional armchair pattern — apply only when the current reference actually contains an armchair with two visible front posts: place both knees between the two front posts, keep the posts visible outside the legs, bring both legs over the front edge of the seat, and separate the shoes across foreground and midground. Do not make exact limb-over-post occlusion a success condition unless the requested composition truly requires it; a narrow post crossing a thigh, knee, or calf raises the risk of an anatomically impossible furniture intersection. Do not transfer this geometry to references without that exact chair structure.

Use `画面左侧` and `画面右侧` instead of relying on the subject's left and right. Define the foreground hero shoe once and keep that assignment unchanged throughout the prompt.

### Walking frame

Specify the leading foot, trailing foot, weight transfer, stride direction, and camera direction. Ask for a crisp captured moment with credible ground contact. Use 28–35 mm for environmental movement or 35–50 mm for cleaner catalog motion.

### Product detail

Use a 50–85 mm look and frame around the knee, ankle, and shoe. Keep the hero shoe complete and show only visible material, surface, side-profile, or sole details. Preserve construction and branding; do not infer features hidden in the reference.

## Designing a shot set

Choose a mix that fits the reference environment and the requested count. Cover distinct product stories rather than filling a quota. A balanced 10-shot set might contain:

- 3 natural or mild-wide standing images;
- 2 seated or supported poses, only if the scene supports them;
- 2 walking or transitional moments;
- 1 high-angle image;
- 1 low-angle shoe hero;
- 1 product detail.

For larger sets, add environment-led creative frames, alternate sides of the product, and restrained variations within each family. Do not force every available pattern into a small set.

Before finalizing, check that adjacent shots differ meaningfully in at least three of these dimensions:

- pose family;
- camera height or direction;
- lens character;
- crop or subject scale;
- which shoe surface is communicated;
- emotional or commercial purpose.

Keep campaign continuity across the set: same person, exact shoe product, outfit, scene logic, lighting family, color treatment, and overall retouching character.

## Common conflict pairs

Avoid stacking these unless the user explicitly prioritizes the tradeoff:

- rigid symmetrical standing + extreme low angle + oversized foreground shoe;
- both shoes equally dominant + one shoe extremely close to lens;
- exact catalog proportions + dramatic ultra-wide distortion;
- tight shoe detail + full-body pose readability;
- strong overhead evidence + low-horizon environmental depth;
- large pose change + exact preservation of the original silhouette.

When a conflict is requested, state the winning priority and simplify the losing requirement.

## Clean photographic output

When the reference contains overlaid marketing text or watermarks and the user wants a clean photograph, describe the desired pixels positively:

> 输出为纯摄影画面，原文字覆盖区域由连续自然的墙面、地面或背景纹理填充；只保留真实存在于场景中的人物、服装、鞋类产品、家具和环境元素。

Do not remove physical signage or genuine branding printed on the product.
