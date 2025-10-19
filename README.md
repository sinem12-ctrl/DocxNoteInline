# 📘 Word Footnote Inline Tool

This project moves **footnotes** (and optionally **endnotes**) from `.docx` (Microsoft Word) files **inline into the text**.  
Instead of the footnote number, the footnote text is inserted **inside parentheses**.  
Footnotes longer than 200 characters are skipped, and the footnote list at the end of the Word file is completely cleared.

---

## ⚙️ Features

- 🧩 Removes footnote numbers and inserts inline text instead.  
- ✂️ Skips footnotes longer than 200 characters.  
- 🧼 Completely clears the footnote list (`footnotes.xml`, `endnotes.xml`).  
- 🗂️ Can process a single `.docx` file or all files in a folder.  
- ⚡ Skips corrupted or incompatible files safely.  

---

## 🚀 Usage

### 🔹 Single File

```python
# Specify input and output file paths
input_file = r"input_single_word_file.docx"
output_file = r"output_single_word_file.docx"

# Process the file
process_docx(input_file, output_file, include_endnotes=False)
```

### 🔹 Process All Files in a Folder

```python
input_folder = r"input_folder_path"
output_folder = r"output_folder_path"

result = process_folder(
    input_folder,
    output_folder,
    include_endnotes=False,
    suffix="_v1"  # suffix added to output file name
)

print(result)  # shows summary info
```

---

## 📂 File Structure

```
project_folder/
│
├── inline_footnotes.py     # Main Python script
├── input_folder/           # Input files
└── output_folder/          # Processed files
```

---

## ⚠️ Notes

- The 200-character limit can be adjusted via `MAX_NOTE_LEN`.  
- Non-`.docx` files are skipped automatically.  
- Temporary files created by Word (`~$`) are ignored.  
- Only Office Open XML `.docx` files are supported.  

---

## 🖥️ Example Terminal Output

```
OK  : input_folder/example.docx  ->  output_folder/example_v1.docx  | 4 footnotes added
SKIP: input_folder/~$temp.docx
FAIL: input_folder/broken.docx  (BadZipFile)

Summary
 Processed files: 5
 Footnotes added: 18
 Skipped/incompatible: 2 files
```

---

## 📜 License

This project is released under the **MIT License**.  
You are free to use, modify, and distribute it.
