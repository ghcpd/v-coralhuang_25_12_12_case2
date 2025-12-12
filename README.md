Enhanced Notes Organizer

Overview
--------
This project provides an enhanced single-page notes organizer that implements and extends the behaviors of the provided input.html drag-and-drop portlets app. The enhanced implementation improves visuals and adds features requested in the task:

- Add/Delete notes (per-column)
- Inline editing (double-click header or content)
- Scrollable long note content (fixed max-height with overflow)
- Import and Export layout as JSON (preserves header, content, label)
- Initializes from provided example-layout.json (embedded fallback included)
- Labels / color coding preserved during import/export
- Search bar for live filtering by header or content
- Undo last delete (one-level undo)
- Drag-and-drop between columns and re-ordering preserved
- Collapse / Expand notes

Files
-----
- enhanced_app.html — The enhanced implementation (self-contained). It attempts to load example-layout.json from the same folder; if unavailable it falls back to the embedded layout identical to the provided JSON.
- README.md — This document.

How to run
----------
1. Place enhanced_app.html and example-layout.json in the same folder (already present in the workspace).
2. Open enhanced_app.html in a modern browser. (If your browser blocks local fetch, the page contains an embedded fallback copy of the JSON so it will still start in the expected imported state.)

Interactive features (quick guide)
---------------------------------
- Add note: Click the "+ Add" button on a column, provide the title and label, then click "Add".
- Delete: Click the ✕ button inside a note's header. A toast appears telling you an undo is available.
- Undo last delete: Click the "Undo Delete" button in the footer (one-level undo only).
- Edit notes: Double-click a header or content to edit inline; changes are saved automatically when focus leaves the field.
- Labels / Color: Click the small color swatch on a note header to choose a label (important, idea, default, personal, reference, study). The label and its color are preserved in exports.
- Search / Filter: Use the search box in the top-right to filter notes by header or content in real time.
- Collapse / Expand: Use the ▾ icon on the note header to collapse or expand the content area.
- Drag & Drop: Drag notes by their header to reorder within a column or move to another column.
- Export JSON: Click "Export" to copy layout JSON to console and "Download Exported JSON" to download a file. The exported structure follows the same schema as example-layout.json.
- Import JSON: Click "Import" and select a JSON file formatted similar to example-layout.json. The UI will re-initialize from that file.
- Reset: Click "Reset" to restore the built-in original layout.

Technical & design notes
------------------------
- The app uses jQuery + jQuery UI (sortable) for drag-and-drop behavior for broad compatibility.
- The app serializes/deserializes layout as a JSON object: { columns: [ { id, notes: [{header,content,label}] } ] }.
- On page load, the app first attempts to fetch example-layout.json from the same folder. If fetch fails (e.g., file:// restrictions), the embedded layout is used so the UI always starts in the expected imported state.
- All interactions are DOM-driven, and the export function derives the current layout from the DOM state to ensure the exported JSON reflects current order and content.
- Visual improvements include rounded corners, subtle shadows, modern typography (Inter via Google Fonts), colored label styles, hover/drag cues, and consistent spacing.

Notes
-----
- input.html from the original project is left unchanged in the workspace as requested.
- No build tools are required — enhanced_app.html is self-contained and relies on CDN-hosted jQuery and jQuery UI only (no client-side frameworks).

If you want small changes or an added feature (e.g., label creation UI or multi-level undo), tell me the preference and I can iterate quickly.
