# Subtitles and On-Screen Type

Use this reference for subtitles, accessibility captions, lower thirds, names/titles, supers, quote/data cards, credits, kinetic type, and localization. Do not collapse them into one decorative “text style.”

## 1. Classify Text by Job

- **Accessibility captions:** speech plus required speaker or non-speech information; accuracy, timing, reading, localization, and delivery mode dominate.
- **Editorial subtitles:** translated or editorial dialogue text; preserve meaning, timing, shot context, and language conventions.
- **Lower thirds/identifiers:** names, roles, locations, sources, or live status; hierarchy and update behavior dominate.
- **Supers/labels/data:** facts, dates, quotes, chapter labels, calls to action, disclaimers, and data callouts.
- **Credits/legal:** dense or duration-bound information with strict content and rights requirements.
- **Display/kinetic type:** expressive title or campaign typography; never use it to weaken required caption readability.

## 2. Build the Type Contract

For each text class record:

```markdown
| Text class | Content source | Type role/font/fallback | Size/spacing logic | Width/line behavior | Color/background/edge | Placement/safe rule | Motion/timing | Editable/localized | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
```

Use the target platform or client specification for exact limits. Do not invent one universal font size, character count, line count, or safe-zone percentage across formats.

## 3. Stress Content

Test with real or approved representative extremes:

- Longest name, title, organization, location, disclaimer, and data value.
- Short one-word labels and mixed numeric/text content.
- Fast dialogue, pauses, interruptions, overlapping speakers, songs/music, sound descriptions, and off-screen speakers when applicable.
- Light, dark, low-contrast, textured, moving, face-heavy, and graphics-heavy backgrounds.
- Small-screen/mobile preview and viewing at realistic distance.
- Multiple languages, text expansion, CJK/Latin mixtures, RTL or bidirectional text, accents/diacritics, and missing-glyph fallback when scoped.

## 4. Timing and Segmentation

- Align caption and subtitle timing to real speech and editorial intent, not arbitrary animation beats.
- Break at meaningful linguistic boundaries and avoid timing or line breaks that change meaning.
- Define behavior around cuts, transitions, speaker changes, rapid dialogue, and overlapping on-screen graphics.
- Preserve enough exposure for comprehension according to the target captioning standard and actual content; verify rather than assuming.
- Keep decorative entrance/exit motion subordinate to reading. Provide a stable or quiet result when motion would impair access.

## 5. Placement and Collision

- Define title/action/safe regions from the actual delivery specification and representative platform UI.
- Reserve collision rules among subtitles, lower thirds, bugs, CTAs, credits, faces, key action, and platform overlays.
- Allow placement to adapt when footage or simultaneous graphics make the default region unusable.
- Ensure background boxes, shadows, outlines, masks, or gradients solve real contrast conditions without obscuring essential imagery.

## 6. Delivery and Localization

- Record burned-in versus sidecar/closed-caption deliverables and which source is authoritative.
- Preserve text, timing, speaker/SDH metadata, language identifiers, and style capabilities supported by the required format.
- Keep translated copy editable and define who approves linguistic meaning versus visual fit.
- Do not shrink text indefinitely to absorb translation. Reflow, shorten through approved editorial process, change layout, or create a language-specific master when needed.

## Verification Gate

Do not approve the type system until representative text is readable over real imagery, timing is checked against actual audio/video, collisions are exercised, required scripts render correctly, accessible captions remain distinct from decorative text, and exported/burned-in/sidecar outputs behave as specified.
