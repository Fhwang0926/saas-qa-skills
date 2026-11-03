# UI and accessibility review

Adapted from the scope of Vercel's web-design-guidelines and informed by W3C WAI's preliminary accessibility checks; see [sources](sources.md). Apply relevant checks to the requested pages and states rather than treating this list as a complete audit.

## Interaction and forms

- Check that links, buttons, and controls communicate their purpose and work with keyboard navigation. Look for visible focus, sensible focus order, and focus handling in dialogs, menus and validation errors.
- Check meaningful labels, input types, required fields, error placement and recovery. Verify that users can understand loading, success and failure states, and that repeated submissions are handled appropriately.
- Check navigation, back/forward behavior and deep links where relevant. Avoid triggering destructive or externally visible actions without authorization.

## Visual and responsive behavior

- Inspect actual content at relevant desktop and mobile sizes. Look for clipped text, awkward line breaks, horizontal overflow, obscured controls, overlap, and touch targets that are difficult to use. Consider translated and longer content when it is present.
- Check that text and essential UI indicators remain distinguishable, images have suitable alternatives, headings convey structure, and zoom does not hide content or controls. Check reduced-motion behavior when motion is relevant.
- When relevant to the requested pages, inspect the page title and language, skip navigation, form labels and required-field indications. For in-scope video or audio, note whether captions or transcripts are available. Report only what was actually inspected; these checks do not establish compliance.
- Compare changes with the product's existing visual language and interaction patterns. Treat design preferences as suggestions, and distinguish them from reproducible usability or accessibility barriers.

## Evidence and limits

- Record the page, viewport, browser, relevant state, steps and observed impact. Include a source file and line when code establishes the cause; do not infer a runtime failure from code alone.
- Automated scans and quick manual checks can reveal barriers but cannot establish full accessibility or WCAG compliance. List assistive technology, browsers, roles and states that were not checked.
