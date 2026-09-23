# Prompt template

Write seven short sentences, always in this order. Generators give more weight to what comes first, so the subject and its identity lead.

```
1 Subject:  {subject as seen, with one visual detail}, {framing}, {position in frame}.
2 Identity: Keep the face, hair and clothing identical to the reference image.   ← people
            Keep its shape, materials and proportions identical to the reference image.   ← objects
3 Motion:   {Subject} {main action}[, then {follow-up}], {pace}[, {ambient motion}].
            [It gradually transforms into {X} over the full {N} seconds, one continuous change with no sudden jumps.]
            [Hands stay relaxed and clearly formed.]
            [Each person keeps their own position and appearance.]
4 Camera:   {one camera move}.
5 Light:    {requested light, or light read from the photo}, consistent with the reference.
            (if Relight fired: subtle {look} color grade, light direction unchanged from the reference)
6 Style:    {one style}[, neutral modifiers][, variant additions].
7 Timing:   {N}-second clip, {aspect} framing as in the source, one continuous shot.
```

If the user didn't give a pace, write "slowly and naturally". Don't add a pace if the action already contains one ("drives slowly").

If there's no action, write "Subtle natural movement, gentle breathing and small shifts in posture" for people, or "subtle natural movement" for objects.

## Variants

| | Safe | Cinematic | Social |
|---|---|---|---|
| Purpose | Most reliable result | Film look | Stops the scroll |
| Actions | first action only | up to 2 | up to 2 |
| Pace | slowly and naturally | as requested, controlled | clear, energetic but smooth motion |
| Default camera | locked-off static camera | slow dolly-in with shallow depth of field | quick, smooth push-in in the first second |
| Camera if Motion overload fired | locked-off static camera | keep one gentle move | keep one gentle move |
| Added style | none | cinematic color grade, subtle film grain (or "cinematic composition" for stylized looks) | crisp detail, punchy contrast |

## Negative prompt

Always include:

`morphing, flicker, warped face, distorted anatomy, extra limbs, sudden cuts, jitter, watermark, text`

Add the following when the matching condition applies:

| Condition | Add |
|---|---|
| A person is in frame, or hands are involved | `warped hands, extra fingers` |
| Text was requested | `letters, captions, logos` |
| Multiple subjects | `merging bodies, swapped faces` |
| Source quality issue | `noise, blur` |
| Style conflict resolved to photorealistic | the dropped styles, e.g. `cartoon, anime` |

## Worked example

**Photo:** vertical 9:16, a girl in a dress standing on a beach at sunset, centered, medium shot, warm and bright.
**Request:** "make the girl walk toward the camera, wave and smile then turn around, anime style but realistic, with a sign that says SUMMER, zoom in then zoom out, make it night"

**Clarity:** 6 → 97. Issues found: action overload, style conflict, text in frame, relight, hands, camera conflict, motion overload.

**Safe:**
The girl in the light dress, medium shot, centered in the frame. Keep the face, hair and clothing identical to the reference image. The girl walks toward the camera, slowly and naturally. Hands stay relaxed and clearly formed. Locked-off static camera. Subtle night color grade, light direction unchanged from the reference. Photorealistic. 5-second clip, 9:16 framing as in the source, one continuous shot.

**Negative:** morphing, flicker, warped face, distorted anatomy, extra limbs, sudden cuts, jitter, watermark, warped hands, extra fingers, text, letters, captions, logos, cartoon, anime

**Before you generate:** add "SUMMER" afterwards with CapCut's text tool. Waving, smiling and turning around were dropped: try them as a second clip that starts from this one's last frame.
