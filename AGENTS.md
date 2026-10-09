# Portfolio Development Rules for Codex

These instructions apply to all work inside `web-dev-portfolio/`.

## 1. Preserve the Existing Design

- Follow the established design system, typography, colors, spacing, and visual hierarchy.
- Do not redesign existing sections unless explicitly requested.
- Prefer small, targeted changes over broad rewrites.
- Do not modify unrelated components or files.
- Reuse existing CSS variables and conventions.

## 2. CSS Writing Style — Mandatory

Write CSS in a readable, expanded format.

- Use 4 spaces for indentation.
- Write one CSS declaration per line.
- Put opening braces on the same line as selectors.
- Put closing braces on their own lines.
- Use blank lines between CSS rules.
- Use descriptive section comments to organize styles.
- Group related selectors when appropriate.
- Expand media queries and their declarations across multiple lines.
- Do not minify CSS or compress multiple rules into one line.
- Follow the formatting conventions already established in the stylesheet.

Example:

```css
/* ========================================
   ARTICLE SCREENSHOTS
======================================== */

.cs-figure {
    width: 100%;
    margin-block: 12px 32px;
}

.cs-figure img {
    display: block;
    width: 100%;
    height: auto;
    border-radius: 8px;
}
```

## 3. Layout and Image Sizing

Always inspect the parent container and surrounding content before assigning element widths.

- Respect existing content-column widths.
- Images inside articles should normally stay within the article column.
- Do not make screenshots wider than their section without explicit approval.
- Hero images may use a wider layout when the existing design supports it.
- Use `max-width`, responsive widths, and natural aspect ratios.
- Avoid arbitrary fixed heights or unnecessary cropping.
- Do not stretch or upscale small screenshots.
- Size images according to their content and purpose, not simply their source resolution.
- Compact UI screenshots should not be displayed at the same scale as full application screenshots.
- Keep captions visually aligned with their corresponding images.
- Avoid negative margins, absolute positioning, or transforms solely to force oversized images outside their containers.

If a wider image would materially improve a section, explain the proposed exception before implementing it.

## 4. Responsive Design — Mandatory

Every layout change must be evaluated at:

- 360px — small mobile
- 768px — tablet
- 1024px — laptop
- 1440px — desktop

Check that:

- No content overlaps.
- No horizontal overflow occurs.
- Text remains readable.
- Images remain proportional.
- Buttons and links remain accessible.
- Spacing and alignment remain visually balanced.
- Screenshots do not overpower the text surrounding them.

A technically valid layout is not automatically a visually acceptable layout.

## 5. Visual Verification

For any change affecting layout, spacing, typography, images, or responsive behavior:

1. Inspect the rendered page in a browser when browser tools are available.
2. Capture or inspect screenshots at relevant viewport sizes.
3. Compare the result with the surrounding sections.
4. Correct obvious visual regressions before reporting completion.

Do not claim visual verification was completed if the browser was unavailable or screenshots were not inspected.

If browser verification is unavailable, clearly state that visual QA is pending.

## 6. Maintainability

- Prefer simple CSS over complicated positioning techniques.
- Avoid unnecessary selector specificity.
- Do not introduce duplicate or conflicting rules.
- Remove obsolete CSS when replacing an implementation.
- Preserve semantic HTML and accessibility features.
- Do not introduce new dependencies for simple layout changes.
- Keep the implementation understandable to a junior frontend developer.

## 7. Technical Accuracy

For project case studies:

- Verify technical claims against the current project source.
- Do not repeat outdated implementation details or resolved defects.
- Do not invent functionality, testing results, or performance metrics.
- Clearly distinguish live API behavior from manually configured test scenarios.
- Use the current canonical repository links.
- Do not expose credentials or introduce security-sensitive details unnecessarily.

The canonical PIT STOP repository is:

https://github.com/jbalagantio/PIT-STOP

## 8. Completion Requirements

Before reporting a task as finished:

1. Review the final code for formatting consistency.
2. Check for unnecessary changes.
3. Verify relevant links and asset paths.
4. Perform responsive and visual QA when possible.
5. Report any checks that could not be completed.

The final report must briefly state:

- Files modified.
- Changes made.
- Verification performed.
- Any remaining limitations or unverified behavior.

## 9. Project Priority

The current priority is completing and publishing Portfolio V1.

Favor launch readiness, correctness, readability, and maintainability over unnecessary polish.

Do not initiate additional redesigns, feature expansions, or architecture changes without explicit instructions.