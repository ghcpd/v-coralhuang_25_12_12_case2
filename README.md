# Enhanced Notes Organizer

Overview
- This project provides an enhanced single-file implementation (enhanced.html) of a drag-and-drop notes organizer. It preserves the behaviors in the original `input.html` while adding several features: add/delete/edit notes, label/color-coding, scrollable note content, import/export JSON, search/filter notes, and a one-level undo for deletes. The UI is modernized with rounded corners, shadows and clearer controls.

Files
- enhanced.html: The enhanced implementation. It loads `example-layout.json` on startup and reconstructs the layout.
- example-layout.json: Sample layout used to initialise the enhanced app. (Not modified.)
- input.html: The original file remains unchanged and is present in the workspace for reference.

Main Improvements
- Add notes: Use the controls in the header to create new notes in a chosen column. Each note is editable and draggable.
- Delete notes: Click ✕ in a note header to delete it. Use Undo to restore the last deleted note.
- Edit notes: Click the ✎ icon to edit title, content and label.
- Labels & color-coding: Select a label while creating or editing a note; the label dot and data are preserved on import/export.
- Scrollable content: Note content areas are constrained with a max height and `overflow: auto` to handle long notes.
- Import/Export JSON: Export the current layout to a downloadable JSON file. Import a JSON file to reconstruct the layout.
- Search / Filter: Use the search input to filter notes in real time by header or content text.
- Drag-and-drop: Notes can be dragged between columns and re-ordered; the header is the drag handle.
- UI Enhancements: Updated spacing, shadows, fonts and colors for a cleaner UX.

How to Run
1. Serve the directory so the browser can fetch `example-layout.json`. In the project directory run a simple static server. For Python 3:

```powershell
# Start a static server in the current directory
python -m http.server 8000
```

2. Open a browser at `http://localhost:8000/enhanced.html`.

Note: Opening the file via `file://` may block fetch requests for `example-layout.json`. Helpful option: use a lightweight file server like the Python command above.

Using the App
- Add a note: Select the column in the dropdown, set a title and label, and click `Add`.
- Delete a note: Click the ✕ button in the note header. Use `Undo` to restore the most recent deletion.
- Edit a note: Click the ✎ icon in the header to edit the title, content and label. Click `Save`.
- Collapse/Expand: Click the ▾ button in the header to hide or show the content.
- Re-order: Drag the note by the header to reorder or move it across columns.
- Scroll within a note: Long content scrolls inside each note area (max height enabled).
- Search: Type in the search box to filter notes in real time by header or content.
- Export: Click `Export` to download the current layout as a JSON file.
- Import: Click `Import` and choose a JSON file matching the structure to rebuild the layout.

Data Format
The internal JSON structure is simple:

```
{ "columns": [ { "id": "col-1", "title": "Today", "notes": [{"header":"Header","content":"Text","label":"idea"}] } ] }
```

Constraints & Notes
- The app uses jQuery and jQuery UI (CDN) for sortable functionality and DOM helpers; no build step is required.
- The app will attempt to fetch `example-layout.json` on load and initialize the layout accordingly.
- This implementation preserves the note label data (for colors) in import/export.
- Undo supports only a single most recent delete (one-level undo).

Design Decisions
- No external build tools or frameworks were used; everything is in a single `enhanced.html` file for simplicity and portability.
- To keep behaviour consistent with the original project, drag/hide operations still behave around the header area; edit/delete are accessible from the header.

Next Steps / Enhancements
- Add multiple-level undo/redo stack.
- Add persistent storage using localStorage or server persistence.
- Add accessible keyboard interactives and better mobile responsiveness.

If you want me to add anything else (e.g., localStorage persistence, richer label editing, or a download preview), tell me and I’ll implement it.
