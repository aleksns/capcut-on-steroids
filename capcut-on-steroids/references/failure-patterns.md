# The 14 failure patterns

These are ordered by severity. **Fixable** rules are solved in the prompt. **Source** rules depend on the image itself: tell the user what to change.

| # | Rule | Severity | Type |
|---|---|---|---|
| 1 | Action overload | High | fixable |
| 2 | Style conflict | High | fixable |
| 3 | Text in frame | High | fixable |
| 4 | Transformation | High | fixable |
| 5 | Relight | Medium | fixable |
| 6 | Hands | Medium | fixable |
| 7 | Camera conflict | Medium | fixable |
| 8 | Motion overload | Medium | fixable |
| 9 | Multiple subjects | Medium | fixable |
| 10 | Vague subject | Medium | fixable |
| 11 | Aspect mismatch | Medium | source |
| 12 | Long prompt | Low | fixable |
| 13 | Source quality | Low | source |
| 14 | No camera direction | Low | fixable |

---

## 1. Action overload: High

**Fires when** the request has more distinct actions than the clip can hold: more than 2 for 5 seconds, or more than 3 for 10 seconds. Ambient motion (hair, water, leaves) doesn't count.
**Why it fails:** models finish one or two actions and leave the rest half-done or blended together.
**Fix:** keep the first action as the main motion, plus at most one follow-up ("…, then waves"). Safe keeps one. Name the dropped actions to the user.

## 2. Style conflict: High

**Fires when** a realistic style (photorealistic, realistic, lifelike) is combined with a stylized one (anime, cartoon, 3D/Pixar, claymation, painterly), or when two stylized styles are combined.
**Why it fails:** the model alternates between both looks, which flickers.
**Fix:** keep the first style mentioned and put the other in the negative prompt. Neutral modifiers such as *cinematic*, *vintage film* and *black and white* can stay.

## 3. Text in frame: High

**Fires when** the request asks for readable words: a sign that says X, a caption, a title, a logo, or anything in quotes.
**Why it fails:** generators draw letters as shapes, so text comes out garbled and shifts between frames.
**Fix:** remove it from the prompt and add `text, letters, captions, logos` to the negative. Tell the user to add the text afterwards with CapCut's text tool.

## 4. Transformation: High

**Fires on** "turns into", "transforms", "morphs", "becomes", "changes into".
**Why it fails:** this is where image-to-video breaks most often. Shapes melt and identities drift.
**Fix:** write it as one slow, continuous change across the whole clip: *"It gradually transforms into a flower over the full 5 seconds, one continuous change with no sudden jumps."* Suggest also trying it as two separate clips.

## 5. Relight: Medium

**Fires when** the requested lighting contradicts the photo: night on a bright image, daylight on a dark one, golden hour on a cool, bright scene.
**Why it fails:** relighting the whole frame makes the model repaint every frame, which flickers.
**Fix:** ask for a *subtle {look} color grade, light direction unchanged from the reference*.

## 6. Hands: Medium

**Fires on** waving, clapping, holding, grabbing, pointing, typing, playing an instrument, eating or drinking, or any mention of hands and fingers.
**Why it fails:** hands are the hardest thing for video models. Expect extra fingers and warping.
**Fix:** add *"Hands stay relaxed and clearly formed"* and put `warped hands, extra fingers` in the negative.

## 7. Camera conflict: Medium

**Fires when** there are opposing moves (push in + pull out, pan left + pan right, tilt up + tilt down), or more than one camera move of any kind.
**Why it fails:** one short shot can't do both, so the model picks one at random or jitters between them.
**Fix:** keep the first move.

## 8. Motion overload: Medium

**Fires when** the camera moves and the subject also moves a lot (a fast pace, or more than one action).
**Why it fails:** the subject and background smear.
**Fix:** Safe uses a locked-off camera. Cinematic and Social keep one gentle move.

## 9. Multiple subjects: Medium

**Fires on** two, both, couple, group, crowd, friends, people, together.
**Why it fails:** faces and bodies merge or swap during motion.
**Fix:** add *"Each person keeps their own position and appearance"*. If you can see the photo, describe each person by position ("the man on the left in grey"). Put `merging bodies, swapped faces` in the negative.

## 10. Vague subject: Medium

**Fires when** no subject is named ("make it move", "animate this") or the request is under four words.
**Why it fails:** the model decides what to animate, often the background.
**Fix:** name the subject from what you see in the photo, including a visual detail and its position.

## 11. Aspect mismatch: Medium, source

**Fires when** the platform doesn't fit the image: vertical platforms (TikTok, Reels, Shorts, Stories) with a square or landscape photo, or widescreen platforms (YouTube) with a portrait or square one.
**Why it fails:** the model keeps the source framing, so the clip won't fill the screen.
**Tell the user:** crop to the target ratio before uploading. The prompt keeps the source ratio.

## 12. Long prompt: Low

**Fires when** the request is over about 45 words.
**Why it fails:** later instructions get less weight than the first ones.
**Fix:** the template compresses it into short, ordered sentences.

## 13. Source quality: Low, source

**Fires when** the short side is under 720 px, the image is very dark, or it is very low in contrast.
**Why it fails:** motion amplifies noise and smears soft detail.
**Tell the user:** use a sharper or brighter version if they have one. Add `noise, blur` to the negative.

## 14. No camera direction: Low

**Fires when** no camera move or static shot is specified.
**Why it fails:** the model picks a move for you, often a drift or zoom you didn't want.
**Fix:** each variant sets its own default camera (see the template).
