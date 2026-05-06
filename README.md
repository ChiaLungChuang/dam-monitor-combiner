# 🪰 DAM Monitor Combiner

A browser-based tool for combining Drosophila Activity Monitor (DAM) data from three synchronized monitors into a single output file. Built with [Shinylive](https://posit-dev.github.io/r-shinylive/) — runs entirely in your browser, no installation required.

🔗 **[Launch the app](https://chialungchuang.github.io/dam-monitor-combiner/)**

---

## What it does

DAM experiments often run the same cohort of flies across three synchronized monitors. This tool:

1. Accepts three Monitor `.txt` files as input
2. Keeps metadata columns (V1–V10) from the first file unchanged
3. Sums activity counts (V11–V42) across all three monitors row by row
4. Exports a single combined `.txt` file in the original DAM format

---

## How to use

No installation needed — just open the link above in any browser.

| Step | Action |
|------|--------|
| 1 | Open the app in your browser |
| 2 | Upload Monitor 1, Monitor 2, and Monitor 3 `.txt` files using the three file pickers |
| 3 | Click **▶ Run Combination** |
| 4 | Review the preview table to verify the output |
| 5 | Click **⬇ Download** to save the combined file |

> Files are processed entirely within your browser and are never uploaded to any server.

---

## Input file requirements

- Tab-separated `.txt` files exported directly from DAM System 2 or compatible software
- All three files must cover the **same time window** (identical row counts)
- Each file must contain at least 42 columns (V1–V42)

---

## Output

The combined file is saved as `[Monitor1_filename]_combined.txt` in your Downloads folder, in the same tab-separated format as the original DAM files — compatible with downstream analysis tools including Rtivity and custom R pipelines.

---

## Technical details

| | |
|---|---|
| Built with | R + Shiny + Shinylive (WebAssembly) |
| Runs on | Any modern browser (Chrome, Firefox, Safari, Edge) |
| Data privacy | All processing is local — no data leaves your browser |
| Dependencies | None for end users |

---

## For developers

To modify and redeploy:

```r
# 1. Edit app.R

# 2. Re-export
install.packages("shinylive")  # if needed
shinylive::export(
  appdir = "path/to/app/",
  destdir = "path/to/app/site"
)

# 3. Push to GitHub
cd path/to/site
git add .
git commit -m "Update app"
git push
```

GitHub Pages updates within ~1 minute after each push.

---

## Contact

Demontis Lab · Department of Developmental Neurobiology · St. Jude Children's Research Hospital  
For questions or bug reports, please open a [GitHub Issue](../../issues).
