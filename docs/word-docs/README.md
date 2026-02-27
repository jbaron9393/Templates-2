# Word Docs Folder

Drop `.docx` files into this folder, then define them in `index.json`.

Each entry supports:
- `fileName` (required): exact `.docx` file name in this folder
- `title` (optional): display title shown in the site
- `category` (optional): group label shown in the site

Example:

```json
{
  "files": [
    {
      "fileName": "gi-grossing-manual.docx",
      "title": "GI Grossing Manual",
      "category": "GI"
    },
    {
      "fileName": "gyn-template.docx",
      "title": "GYN Template",
      "category": "GYN"
    }
  ]
}
```

## Notes
- Docs are grouped by `category` in the "Site Documents" section.
- If `title` is missing, the app auto-generates one from the file name.
- For backward compatibility, plain string entries (e.g., `"my-doc.docx"`) still work and will be placed in `Uncategorized`.
