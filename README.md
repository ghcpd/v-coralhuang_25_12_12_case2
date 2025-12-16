# Enhanced Note Organizer

This is an enhanced version of the drag-and-drop note organizer app, built on top of the existing `input.html` implementation. It adds several new features while preserving all original functionality.

## Overview of Enhancements

The enhanced app includes the following improvements over the original:

1. **Add & Delete Notes**: Users can add new notes to any column and delete existing notes with a delete button.
2. **Scrollable Long Notes**: Note content areas have a maximum height with scrollable overflow for long text.
3. **Import & Export as JSON**: Full layout can be exported to JSON and imported from JSON files.
4. **Visual Appearance Upgrade**: Modern UI with improved colors, spacing, shadows, and typography.
5. **Note Labels / Color Coding**: Notes can be assigned labels with corresponding color coding.
6. **Search / Filter Notes**: Real-time search functionality to filter notes by header or content.
7. **Undo Last Delete**: Ability to undo the most recently deleted note.

The app starts in a state reflecting the imported layout from `example-layout.json`.

## How to Use

### Running the App
Open `enhanced_app.html` in a modern web browser. The app will automatically load the initial layout from the embedded JSON data.

### Adding Notes
- Click the "Add Note" button in any column to create a new note.
- New notes are draggable, editable, and deletable.

### Deleting Notes
- Click the "✕" button in the note header to delete a note.
- Deleted notes can be restored using the "Undo Delete" button.

### Editing Notes
- Click on the note header or content area to edit the text inline.
- Changes are saved automatically.

### Assigning Labels
- Use the dropdown in the note header to assign a label (Default, Important, Idea, Personal, Reference, Study).
- The note's border color changes based on the selected label.

### Searching Notes
- Type in the search bar at the top to filter notes in real time.
- Notes are shown/hidden based on whether their header or content contains the search term.

### Dragging and Dropping
- Drag notes by their headers to reorder within columns or move between columns.
- Original drag-and-drop functionality is preserved.

### Collapsing/Expanding Notes
- Click the toggle icon (➖/➕) in the note header to collapse or expand the content area.

### Importing/Exporting Layout
- Click "Export Layout" to download the current layout as a JSON file.
- Click "Import Layout" to load a layout from a JSON file.
- The app starts with the layout from `example-layout.json` embedded.

### Undoing Deletes
- Click "Undo Delete" to restore the most recently deleted note.
- Only one level of undo is supported.

## Technical Notes and Design Decisions

- **Framework**: Built using jQuery and jQuery UI for drag-and-drop functionality, consistent with the original implementation.
- **Styling**: Custom CSS with modern design principles including gradients, shadows, and responsive layout.
- **Data Storage**: Layout data is stored in memory; persistence requires manual import/export.
- **Label System**: Six predefined labels with corresponding CSS classes for color coding.
- **Search**: Case-insensitive search across note headers and content.
- **Undo**: Simple stack-based undo for deleted notes, storing note data and original column position.
- **Import/Export**: JSON format matches the structure of `example-layout.json`.
- **Initialization**: App loads embedded JSON data on startup to demonstrate imported layout.

## File Structure

- `enhanced_app.html`: The complete enhanced application in a single HTML file.
- `README.md`: This documentation file.
- `input.html`: Original implementation (unchanged).
- `example-layout.json`: Sample layout data for import demonstration.

## Original File Preservation

The `input.html` file remains completely unchanged, as required. All enhancements are implemented in the new `enhanced_app.html` file.