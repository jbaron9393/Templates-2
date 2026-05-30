# How to Update Site Documents (No Coding Needed)

This folder contains the Word documents, PDFs, and images that appear in the Grossing Manual website. The website reads the document list from `index.json`, so the file names and titles in that file must stay accurate.

## The Most Important Rule

**If you are replacing or editing an existing document, keep the exact same file name and folder location.**

For example, if you are updating:

```text
docs/word-docs/Breast/Mastectomy Grossing.docx
```

save the updated Word document with this exact same name:

```text
Mastectomy Grossing.docx
```

and put it back in this exact same folder:

```text
docs/word-docs/Breast/
```

Do not add extra words like `updated`, `final`, `copy`, or a date unless you also update `index.json`. The website uses the file name in `index.json` to find the document. If the file name changes but `index.json` does not, the link can break.

## What You Can Upload

The site supports these file types:

- Word documents: `.docx`
- PDFs: `.pdf`
- Images: `.jpg`, `.jpeg`, `.png`

## Option 1: Edit or Replace an Existing Document

Use these steps when the document is already listed on the website and you only want to update its contents.

1. Find the current document inside `docs/word-docs/`.
2. Open it in Microsoft Word or your normal editor.
3. Make the changes you need.
4. Save the file with the **exact same file name**.
5. Put the saved file back in the **exact same folder**.
6. Do **not** change `index.json` if the file name and folder are unchanged.

### Example

If you update this file:

```text
docs/word-docs/Frozens/Cryostat troubleshooting.docx
```

then the updated file must still be named:

```text
Cryostat troubleshooting.docx
```

and must still be inside:

```text
docs/word-docs/Frozens/
```

## Option 2: Rename an Existing Document

Only do this if the document really needs a new file name. If possible, keep the old name to avoid breaking links.

If you rename a document, you must update `index.json` too.

1. Rename the actual file in its folder.
2. Open `docs/word-docs/index.json`.
3. Find the matching document entry.
4. Update the `fileName` value so it matches the new folder and file name exactly.
5. Update the `title` value only if you want the name shown on the website to change.
6. Save `index.json`.

### Example Rename

If the file changes from:

```text
Frozens/Cryostat troubleshooting.docx
```

to:

```text
Frozens/Cryostat Troubleshooting Guide.docx
```

then the entry in `index.json` must change from:

```json
{
  "fileName": "Frozens/Cryostat troubleshooting.docx",
  "title": "Cryostat Troubleshooting",
  "category": "Frozens"
}
```

to:

```json
{
  "fileName": "Frozens/Cryostat Troubleshooting Guide.docx",
  "title": "Cryostat Troubleshooting",
  "category": "Frozens"
}
```

Notice that the `title` did not have to change. The `title` is what people see on the website. The `fileName` is where the website finds the file.

## Option 3: Add a New Document

Use these steps when you want to add a brand-new document to the website.

1. Decide which category/folder the document belongs in.
   - Example folders include `Breast`, `Frozens`, `GI 1,2&3`, `GYN-OB 1&2/GYN1`, and `Heart`.
2. Put the new file inside the correct folder under `docs/word-docs/`.
3. Open `docs/word-docs/index.json`.
4. Add a new entry inside the `files` list.
5. Make sure the new entry has:
   - `fileName`: the exact folder path and file name, starting from inside `docs/word-docs/`
   - `title`: the name you want people to see on the website
   - `category`: the category section where it should appear on the website
6. Save `index.json`.

### Example New Document

If you add this new file:

```text
docs/word-docs/Breast/New Breast Protocol.docx
```

then add this entry to the `files` list in `index.json`:

```json
{
  "fileName": "Breast/New Breast Protocol.docx",
  "title": "New Breast Protocol",
  "category": "Breast"
}
```

## Understanding `fileName`, `title`, and `category`

Every document entry in `index.json` usually looks like this:

```json
{
  "fileName": "Breast/Mastectomy Grossing.docx",
  "title": "Mastectomy Grossing",
  "category": "Breast"
}
```

### `fileName`

This is the exact location of the file inside `docs/word-docs/`.

- It must include the folder name if the file is inside a folder.
- It must include the full file name and extension, such as `.docx` or `.pdf`.
- Capital letters, spaces, punctuation, and spelling must match the real file exactly.

### `title`

This is the display name people see on the website.

- Changing `title` changes the name shown on the website.
- Changing `title` does **not** rename the actual Word document.
- You can make the title cleaner than the file name.

### `category`

This controls which section the document appears under on the website.

- The category should usually match the folder or the type of document.
- Use an existing category whenever possible.
- If you add a brand-new category, also add that category name to the `categories` list near the top of `index.json`.

## Adding a Brand-New Category

Only do this if none of the existing categories fit.

1. Create a new folder inside `docs/word-docs/`.
2. Put the new document inside that folder.
3. Open `docs/word-docs/index.json`.
4. Add the new category name to the `categories` list near the top.
5. Add the document entry to the `files` list.
6. Use the same category name in both places.

### Example New Category

If you create this folder and file:

```text
docs/word-docs/Kidney/Kidney Grossing Guide.docx
```

add `Kidney` to the `categories` list:

```json
"Kidney"
```

Then add this entry to the `files` list:

```json
{
  "fileName": "Kidney/Kidney Grossing Guide.docx",
  "title": "Kidney Grossing Guide",
  "category": "Kidney"
}
```

## Quick Checklist Before You Finish

Before saving your changes, check these items:

- The document is inside `docs/word-docs/` or one of its folders.
- The document file name in `index.json` matches the real file name exactly.
- The file extension is included, such as `.docx`, `.pdf`, `.jpg`, `.jpeg`, or `.png`.
- The `title` is spelled the way you want it to appear on the website.
- The `category` is spelled the same way everywhere it is used.
- Commas are correct in `index.json`.
  - Every entry needs a comma after it, except the last entry in the list.

## Common Mistakes That Break the Website Links

Avoid these mistakes:

- Renaming a file but not updating `index.json`.
- Moving a file to a different folder but not updating `index.json`.
- Typing `.doc` instead of `.docx`.
- Forgetting the folder name in `fileName`.
- Adding extra spaces at the beginning or end of a file name.
- Changing a category name in one place but not the other.
- Removing quotation marks or commas from `index.json`.

## Safe Editing Tip

If you are not sure what to change, copy an existing entry in `index.json` from the same category, paste it nearby, and then only change the `fileName` and `title` for the new document.

