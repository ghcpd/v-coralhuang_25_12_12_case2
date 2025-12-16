# Enhanced Notes Organizer — README

Overview
--------
This repository includes an enhanced single-page Notes Organizer implementation (enhanced_app.html) that imports the provided example-layout.json on load and demonstrates an improved user experience over the original portlet-style app.

Key enhancements
- Modernized visual design: rounded cards, shadows, refined spacing and hover cues.
- Add & Delete notes: Add new notes to any column; delete notes with a ✕ button.
- Editable notes: Double-click or focus any note header or content to edit inline (contentEditable).
- Drag-and-drop: Reorder notes within a column and move notes between columns using native drag-and-drop.
- Scrollable long notes: Note content areas have a max-height with overflow:auto and preserve line breaks (white-space: pre-wrap).
- Labels / color coding: Assign labels (Default, Important, Idea, Personal, Reference, Study) to notes; colors are preserved on import/export.
- Search / Filter: Real-time search by header or content text.
- Import / Export JSON: Export the current board to JSON and import a JSON file to rebuild the layout.
- Undo last delete: One-level undo for the most recently deleted note.

Files
-----
- enhanced_app.html — The enhanced implementation (open this file in a modern browser).
- example-layout.json — (provided) The JSON layout automatically imported by enhanced_app.html on load.

Important: input.html is not modified by any deliverable.

How to run
----------
1. Open enhanced_app.html in a modern browser. For best results, serve the directory over HTTP (e.g. with a simple static server) so the automatic import of example-layout.json works without file:// restrictions.

   Example (Python 3):
   - In this folder run: python -m http.server 8000
   - Then open: http://localhost:8000/enhanced_app.html

2. If you open the file via file:// and the example JSON does not load automatically, use the Import button in the top-right and select the included example-layout.json to initialize the board identically.

UI Guide — Interactive features
--------------------------------
- Import (top bar — Import): Load a layout JSON file (structure described below). The app will rebuild the board from that JSON.
- Export (top bar — Export): Download the current board layout as exported-layout.json. The JSON structure is:

  {
    "columns": [
      {
        "id": "col-1",
        "notes": [
          { "header": "...", "content": "...", "label": "important" },
          ...
        ]
      },
      ...
    ]
  }

- Add Note (per column): Click "+ Add Note" in a column to append a new editable note.
- Edit: Double-click or focus the header or content area to edit text. Hit Enter in the header to commit (prevents newline in header).
- Delete: Click the ✕ button in a note header — this removes the note and enables Undo.
- Undo Last Delete: Click "Undo Delete" in the top bar to restore the most recently deleted note to its original column and position (one-level undo only).
- Labels / Color Coding: Use the label selector inside the note header to change the note's label. The small colored dot and label text update instantly. Labels are saved on Export.
- Search / Filter: Type in the search box to filter notes in real time by header or content. Matching notes remain visible; non-matching notes are hidden.
- Drag & Drop: Grab the ≡ handle (or anywhere on the note) and drag to reorder within a column or move to another column. While dragging, a subtle placeholder and card scaling show the drop target.
- Scrollable content: Long note content will show an inner scroll area with a maximum height for tidy columns.

Technical notes & design decisions
---------------------------------
- No external frameworks or build tools are required. The application uses plain HTML, CSS, and vanilla JavaScript.
- Native HTML5 drag-and-drop is used to enable reordering and cross-column movement; this keeps the app framework-free and simple to run.
- Notes are implemented with contentEditable for quick inline editing. Content is exported as plain text (newlines preserved via pre-wrap styling).
- The app attempts to fetch example-layout.json on load. If the page is opened via file:// and fetch is blocked by the browser, use the Import button to load example-layout.json manually.
- Undo is single-level (the most recent deletion only), as required.

JSON import/export compatibility
------------------------------
- The app imports any JSON matching the shape: { columns: [ { id: "...", notes: [ {header,content,label}, ... ] }, ... ] }.
- Labels are preserved as the string value found in the JSON (e.g., "important", "idea"). If an unknown label is encountered, the app falls back to a neutral appearance.

Notes for reviewers
-------------------
- The enhanced_app.html begins by importing the provided example-layout.json (when opened via a standard HTTP server) and will render the identical layout shown in example-layout.json.
- If automatic import fails due to file:// restrictions, import example-layout.json manually using the Import button — the result will be the same.
- input.html remains unchanged in the workspace; this deliverable is a separate enhanced implementation.

Contact / Debug
----------------
Open the browser console and inspect window.NOTES_APP to programmatically interact with the renderer (helpers: renderLayout, exportLayout, LABELS).

Enjoy exploring the enhanced organizer!
