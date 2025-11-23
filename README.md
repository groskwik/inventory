
# 📘 Manual Query Tool – CSV-Based Catalog Search

A lightweight command-line tool to manage your collection of printed manuals.  
The script provides:

- 🔍 Fuzzy search (case-insensitive)
- 🎯 Exact lookup
- 📦 Grouping by storage box
- 🎨 Tracking whether a cover exists
- 🗃️ CSV-based catalog (no hard-coded entries)
- ❌ Remove entries directly from the CLI
- 💾 Automatic persistence to `manuals.csv`

This tool is ideal for quickly answering:

> “Where is the Nikon D50 manual?”  
> “Do I already have a cover for the HP-71 Data Communications manual?”  
> “Show me everything stored in Box 2.”

---

## 📂 Project Structure

```
manual-tool/
│
├── manualtool.py       # Main Python script (CSV-based)
├── manuals.csv         # Your catalog (auto-created on first run)
└── README.md           # Documentation
```

---

## 🗃️ The Catalog — `manuals.csv`

All items are stored in a simple CSV file:

| title | box | cover |
|-------|------|--------|
| HP 71 Owner Manual | BOX 3 | 1 |
| Canon EOS R6 Mark II | BOX 2 | 1 |
| Lowrance Hook Series | | 1 |

- **title** — Name of the manual  
- **box** — `"BOX 1"`, `"BOX 2"`, `"BOX 3"`, or blank  
- **cover** — `1` (has cover) or `0` (no cover)

You can edit the file using:

- Excel  
- LibreOffice  
- Google Sheets  
- VSCode / Notepad  

If the CSV does **not** exist on startup, the script creates an empty one.

---

## ▶️ Running the Tool

Launch the tool:

```bash
python manualtool.py
```

You will see the interactive shell:

```
Manual Query Tool (CSV-based)
Using CSV file: manuals.csv

Commands:
  search <text>
  exact <title>
  list
  list box 1|2|3
  list cover
  remove <text>
  quit
```

---

## 🔍 Commands Overview

### 🔎 `search <text>`
Fuzzy search across all titles.

Examples:

```
> search hp 71
> search nikon 50
> search sapphire
```

Matches are sorted by relevance score.

---

### 🎯 `exact <title>`
Exact, case-insensitive lookup.

```
> exact hp 71 owner manual
```

---

### 📦 `list`
Show all items grouped by:

- BOX 1  
- BOX 2  
- BOX 3  
- COVER (items with cover flag)  
- UNKNOWN (items with neither box nor cover)

```
> list
```

---

### 📦 `list box 3`
List only the contents of a specific box.

```
> list box 3
```

---

### 🎨 `list cover`
List all manuals marked as having covers.

```
> list cover
```

---

### ❌ `remove <text>`
Remove an entry from the catalog and automatically update `manuals.csv`.

Example:

```
> remove hp71
Possible matches to delete:
  1. HP 71 Owner Manual  [box=BOX 3, cover=False, score=0.93]
Number to delete (blank to cancel): 1
Delete 'HP 71 Owner Manual'? [y/N]: y
Removed and updated manuals.csv.
```

You may type exact titles or partial text.

---

### 🚪 `quit`
Exit the program.

---

## 🛠️ Editing `manuals.csv` Manually

You may edit the file directly.

Format:

```
title,box,cover
HP 71 Owner Manual,BOX 3,0
Canon EOS R6 Mark II,BOX 2,1
```

Values meaning:

- `box` can be empty (`""`)
- `cover` accepts: `1`,`0`,`yes`,`no`,`true`,`false`

---

## 💡 Tips for Maintaining Your Catalog

- Keep box names consistent (`BOX 1`, not `box1` or `Box1`)
- Use descriptive titles (same as your eBay listings)
- Leave `box` empty when an item is **cover-only**
- Use the CLI `remove` command instead of manual deletion when possible

---

## 🧩 Potential Future Features

If you want, I can add:

- `add <title>` command  
- Update/edit entries  
- Export the database to HTML for printing  
- Export by box  
- GUI (Tkinter, PyQt, or web app)  
- Barcode scanning (to find manuals instantly)  
- Automatic cover detection from filenames  

Just ask and I’ll implement it.

---

## 👤 Author

Developed by **Benoit Dulauroy**  
Designed to keep your growing manual catalog efficient, searchable, and organized.

---
