# PenniTools PDF Editor v2

## Goal
Provide a browser-first PDF editor with the simplest possible workflow: upload a PDF, see it immediately, click text and type, add text by clicking blank space, format/move/delete text, edit multiple pages, and download.

## Architecture
- PDF.js: render pages and inspect selectable text.
- pdf-lib: create the output PDF.
- Overlay editing is used only as the browser interaction layer; output generation must preserve the original document where possible and explicitly distinguish replacement overlays from true PDF object editing.
- Scanned/image-only pages are detected when no selectable text is returned. They must not be presented as editable text. Such pages require OCR before true text editing can be offered.

## Acceptance tests
1. Upload a normal selectable-text PDF and display it automatically.
2. Click an existing text item and edit it without an Add Text mode.
3. Click a blank area and create text.
4. Apply font, size, bold, italic and colour.
5. Move and delete text.
6. Navigate multiple pages.
7. Download the result.
8. Reopen the downloaded PDF and verify the edited content is present.
9. Detect a scanned page and show an OCR-required message rather than fake text editing.
10. Verify there are no browser console errors during the complete flow.

## Merge rule
Do not merge to `main` until all acceptance tests pass. Production `main` remains the fallback.
