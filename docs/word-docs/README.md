# Word Docs Folder

Drop `.docx` files into this folder, then list each file name in `index.json` under the `files` array.

Example:

```json
{
  "files": [
    "gi-grossing-manual.docx",
    "gyn-template.docx"
  ]
}
```

The site automatically loads this list on page load and renders clickable titles in the "Site Documents" section.
