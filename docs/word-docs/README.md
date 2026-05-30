# How to Update Site Documents (No Coding Needed)

This folder contains the Word documents, PDFs, images, and MP4 videos that appear in the Grossing Manual website. The website reads the document list from `index.json`, so the file names and titles in that file must stay accurate.

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
- Videos: `.mp4`

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

## Option 3: Add a New Document or Video

Use these steps when you want to add a brand-new document, PDF, image, or MP4 video to the website.

1. Decide which category/folder the file belongs in.
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

### Example New Video

If you add an MP4 video, use the same pattern.

If you add this new video:

```text
docs/word-docs/Frozens/Cryostat Cleaning Video.mp4
```

then add this entry to the `files` list in `index.json`:

```json
{
  "fileName": "Frozens/Cryostat Cleaning Video.mp4",
  "title": "Cryostat Cleaning Video",
  "category": "Frozens"
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
- It must include the full file name and extension, such as `.docx`, `.pdf`, `.jpg`, `.png`, or `.mp4`.
- Capital letters, spaces, punctuation, and spelling must match the real file exactly.

### `title`

This is the display name people see on the website.

- Changing `title` changes the name shown on the website.
- Changing `title` does **not** rename the actual Word document, PDF, image, or video.
- You can make the title cleaner than the file name.

### `category`

This controls which section the document appears under on the website.

- The category should usually match the folder or the type of document.
- Use an existing category whenever possible.
- If you add a brand-new category, also add that category name to the `categories` list near the top of `index.json`.

## Adding a Brand-New Category

Only do this if none of the existing categories fit.

1. Create a new folder inside `docs/word-docs/`.
2. Put the new document, PDF, image, or video inside that folder.
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

## Add a New Folder in GitHub

GitHub does not support creating empty folders. A folder must contain at least one file, such as a `README.md`, before GitHub will create and track it.

Use these steps to create a new folder in the Grossing Manual repository:

1. Navigate to the location where you want the new folder to be created.
   - For site documents, this will usually be `docs/word-docs/`.
2. Click **Add file**.
3. Click **Create new file**.
4. In the filename field, type the new folder name followed by `/README.md`.

   Example:

   ```text
   New Folder/README.md
   ```

5. Add a brief description of the folder in the README file.
6. Scroll to the bottom of the page.
7. Enter a commit message describing the addition.
8. Click **Commit new file**.

After committing, the new folder will appear in the repository and can be used to store documents and other files.

### Examples

To create a folder named `Breast`, type:

```text
Breast/README.md
```

To create a folder named `Test`, type:

```text
Test/README.md
```

If you are creating a new site-document category, remember that creating the folder is not enough. You still need to add the category and file entry to `docs/word-docs/index.json`.

## Important Note About MP4 Videos and Mammoth

Mammoth is the tool the website uses to turn Word `.docx` files into readable HTML previews. Mammoth only works with Word documents; it cannot read or convert `.mp4` videos.

MP4 files can still be uploaded to GitHub and listed in `index.json`. The website will show them with a normal video player instead of sending them through Mammoth.

## Quick Checklist Before You Finish

Before saving your changes, check these items:

- The document, PDF, image, or video is inside `docs/word-docs/` or one of its folders.
- The file name in `index.json` matches the real file name exactly.
- The file extension is included, such as `.docx`, `.pdf`, `.jpg`, `.jpeg`, `.png`, or `.mp4`.
- The `title` is spelled the way you want it to appear on the website.
- The `category` is spelled the same way everywhere it is used.
- If you added a new folder/category, the category is also listed in the `categories` list near the top of `index.json`.
- Commas are correct in `index.json`.
  - Every entry needs a comma after it, except the last entry in the list.

## Common Mistakes That Break the Website Links

Avoid these mistakes:

- Renaming a file but not updating `index.json`.
- Moving a file to a different folder but not updating `index.json`.
- Typing `.doc` instead of `.docx`.
- Expecting Mammoth to process `.mp4` videos. Mammoth only processes `.docx`; videos use the browser video player.
- Forgetting the folder name in `fileName`.
- Adding extra spaces at the beginning or end of a file name.
- Creating a new folder but forgetting to add the new category and file entry to `index.json`.
- Changing a category name in one place but not the other.
- Removing quotation marks or commas from `index.json`.

## Safe Editing Tip

If you are not sure what to change, copy an existing entry in `index.json` from the same category, paste it nearby, and then only change the `fileName`, `title`, and `category` values for the new document.
