# Pose Decision System

Use this file when the user requests pose exploration, a multi-shot set, or stronger body-structure diversity. It is a decision system, not a fixed pose catalog and not text to paste verbatim into prompts.

## 0. Present the action menu after route confirmation

Use this menu only after the user explicitly asks for pose exploration or chooses the pose-discovery option in the intent question. Do not assume that an otherwise unexplained image is a color original or that the user wants pose concepts.

Offer exactly 10 numbered action concepts instead of complete prompts. Each concept should be one compact sentence that lets the user roughly visualize the body action, support state, leg arrangement, and footwear presentation. Keep it concise enough to scan; omit reference-role prose, camera specifications, materials, lighting, quality language, negative constraints, and prompt syntax.

Make the 10 concepts meaningfully different and feasible in the visible scene. Do not invent a support or handheld prop that the image does not contain. End by asking the user to reply with one or more numbers; do not expand any concept until they choose.

When the user replies with numbers, expand only the selected concepts into complete standalone Nano Banana 2 prompts using the same original image. Treat the selected concept as a fixed shot brief: retain its defining body action, support state, leg arrangement, and footwear presentation, adding only the camera, composition, reference anchors, and acceptance criteria needed for a complete prompt. Do not replace it with a supposedly better pose. Produce Nano Banana Pro only when explicitly requested. A multi-number reply produces one complete prompt per selected concept.

## 1. Start from the product and the current reference

Choose the footwear message first: balanced pair visibility, one hero shoe, upper/vamp view, side profile, outsole edge, or flex in motion. Select only poses that the visible scene can support and that keep the required shoe surfaces readable.

Reject a pose when it depends on absent furniture, props, rails, steps, walls, or other supports. Product fidelity, credible anatomy, and stable contact outrank pose novelty.

## 2. Build the pose from independent axes

Choose one compatible option from each relevant axis. Do not force every axis into the final prompt when the relationship is already obvious.

### Support state

- free standing or weight shift;
- walking, stepping, turning, or another captured transition;
- seated or perched, only on a support visible in the reference;
- leaning or braced, only against an existing surface;
- crouched or lowered, only when the framing leaves enough room for clear anatomy and shoes.

### Torso direction

- front-facing;
- three-quarter turn;
- profile;
- turned away with a natural look back.

### Leg action

- staggered stance or one foot advanced;
- forward step or cross-step;
- pivot, heel lift, or weight transfer;
- one knee flexed with a clear supporting leg;
- seated legs extended, staggered, or separated in front of the support.

Every leg action needs a believable weight-bearing path, foot landing, and ground or support contact.

### Footwear presentation

- balanced visibility of both shoes;
- one foreground hero shoe and one supporting shoe;
- clean side profile;
- readable upper or vamp;
- visible outsole edge or natural flex in motion.

Do not demand incompatible product views at once. Keep the hero shoe role stable throughout one prompt.

### Upper body and hands

Use the upper body to balance the pose rather than compete with the shoes. Suitable choices include a relaxed empty-hand gesture, hand at the hip, touching hair, adjusting a sleeve, or using a support already visible in the reference. Do not default repeatedly to the same chin-rest or armrest gesture, and do not invent a handheld prop.

## 3. Pass the compatibility gate

Before selecting a pose, confirm:

- the required support or movement space is visible in the current reference;
- body and furniture silhouettes can remain photographically plausible;
- both shoe paths are anatomically connected and their contacts are credible;
- the requested crop can contain the important limbs and complete hero shoe;
- no fragile, exact overlap with a narrow scene structure is required.

Never transfer the geometry of a chair, railing, stair, or other structure from a different image. When an exact occlusion is not essential, separate the important silhouettes.

## 4. Convert the choice into visible geometry

Do not rely on labels such as “dynamic,” “relaxed,” or “fashion pose” alone. State only the visible relationships needed to render the decision:

- torso direction and balance or weight support;
- path of each important leg and where each foot lands;
- frame-relative location and visual role of each shoe;
- hand placement when it affects balance or silhouette.

Use frame-relative left and right when anatomical sides could be misread.

## 5. Create real diversity in a shot set

For each concept, internally track support state, torso direction, leg action, and footwear presentation. Do not expose the matrix unless the user asks for it.

A left/right mirror, a hand swap, or a camera-only change does not by itself create a new pose. Adjacent concepts should change at least two of the four tracked axes. Across a larger set, avoid letting one support state or leg action dominate unless the brief requires it.

Keep identity, exact footwear, outfit, and campaign photography coherent while changing body structure meaningfully.

## 6. Simplify high-risk poses

Reject or simplify combinations that create ambiguous balance, merged shoe contours, limbs crossing narrow structures, impossible foot contact, extreme contortion, or loss of the required product view. Fix the positive geometry first instead of adding a long prohibition list.
