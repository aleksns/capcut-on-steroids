# CapCut on Steroids

A Claude skill that turns a photo and a rough idea into an image-to-video prompt CapCut is hard to misread.

AI video generators fail in predictable ways: too many actions for a short clip, styles that fight each other, text that comes out garbled, lighting the photo doesn't have. This skill reads your photo, checks your request against **14 known failure patterns**, and writes a structured prompt, a negative prompt and three variants.

**Try the web version:** https://aleksns.com/projects/capcut-on-steroids

## What you get

```
Clarity: your prompt 6 → refined 97

What would have gone wrong
- High · Too many actions for 5 seconds: … Fix: kept the first action …
- High · Readable text in the frame: … Fix: removed it; add it in CapCut's text tool …

Prompt (Safe)
The girl in the light dress, medium shot, centered in the frame. Keep the face, hair and clothing identical to the reference image. …

Negative prompt
morphing, flicker, warped face, …

Cinematic and Social variants …
```

## Install

**Claude Code:**

```bash
git clone https://github.com/aleksns/capcut-on-steroids.git
cp -r capcut-on-steroids/capcut-on-steroids ~/.claude/skills/
```

Start a new session, attach a photo and run:

```
/capcut-on-steroids she turns toward the camera and smiles, slow push-in, golden hour
```

Add `duration=10` for a 10-second clip.

**Claude.ai:** zip the `capcut-on-steroids` folder and upload it under *Settings → Capabilities → Skills*.

**Any other LLM:** paste `SKILL.md` and the two files in `references/` into the system prompt.

## How it works

1. **Read:** describe the frame: subject, framing, position, light, palette and quality.
2. **Parse:** split the request into subject, actions, camera, light, style, pace and platform.
3. **Lint:** check the request against the [14 failure patterns](capcut-on-steroids/references/failure-patterns.md).
4. **Compose:** write the prompt in a [fixed order](capcut-on-steroids/references/prompt-template.md): subject → identity → motion → camera → light → style → timing.

## Limits

No prompt guarantees a generation. This skill reduces the common failures and explains why. The rules are based on how image-to-video models generally behave, not on CapCut internals.

## License

MIT © Aleksandr Nazarov
