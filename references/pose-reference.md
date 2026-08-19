# External Pose Reference

Use this file when the user supplies an original footwear-model image and a separate image whose purpose is to guide the person's pose.

## 1. Assign image roles before writing

Honor the user's labels. When the user identifies image 1 as the original and image 2 as the pose reference, keep that mapping exactly; do not reverse it based on upload order or visual simplicity.

- The original image is the sole content source for identity, body characteristics, footwear, outfit, accessories, scene, supports, lighting, color, and photographic character.
- The pose image supplies only the requested body geometry. It does not supply mannequin material, appearance, clothing, props, background, or furniture.
- Transfer camera direction, crop, or subject scale from the pose image only when the user requests those elements too.

State the two roles concisely inside every complete prompt. Never deliver the role statement as a patch that depends on an earlier prompt.

## 2. Read geometry before naming the action

Do not trust a broad semantic pose label when the rendered geometry is what matters. A monochrome mannequin, construction drawing, overlapping silhouette, or foreshortened limb can support several plausible labels and may trigger a familiar but incorrect pose template.

Inspect only the relationships that change the result:

- head direction and gaze when visible;
- torso direction, lean, and balance;
- support points and hand placement;
- relative locations and occlusion order of hips, knees, and ankles;
- path of each lower leg and the landing region of each foot;
- frame-relative displacement between key joints and endpoints.

Use `画面左侧` and `画面右侧` rather than the subject's anatomical left and right when the direction could be confused.

## 3. Resolve ambiguous pose references

When a pose could be misread as a common action, avoid using that action name as the main instruction. Describe three to five decisive visible relationships instead, such as where the knees sit in the frame, which joint is in front, the direction of the lower legs, the distance between ankles, and where the feet land.

Prefer positive geometry. Add one short contrast only when a strong default pose repeatedly overrides the intended geometry; do not accumulate synonyms or a long prohibition list.

If the pose reference and the original scene require different supports, keep only supports visible in the original and adapt the contact points plausibly. Never import furniture or scene structures from the pose reference.

## 4. Keep the prompt compact

A pose-transfer prompt still needs one hero objective. Include:

- a concise statement that fixes the original and pose-reference roles;
- only the body relationships needed to disambiguate the pose;
- camera or crop changes only when requested;
- a few acceptance criteria for anatomy, contact, and shoe readability.

Anchor preserved content to the original instead of re-enumerating it. Nano Banana 2 needs only decisive geometry; Nano Banana Pro may add detail only for genuinely ambiguous occlusion, support, or camera relationships.

## 5. Check before returning

Confirm that:

- every prompt is complete and independently identifies the image roles;
- no generated result has become a source image;
- content comes from the original and pose geometry comes from the intended pose image;
- frame-relative directions and joint relationships agree with the visible pose;
- no semantic pose label contradicts the described geometry;
- the original scene can support the transferred pose without invented furniture or props;
- both required shoes remain anatomically connected, complete, and readable.
