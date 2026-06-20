# 🇹🇷 Double Commander — Turkish Localization

A complete Turkish (TR) localization of [Double Commander](https://doublecmd.sourceforge.io/), an open-source dual-panel file manager. This project was completed as part of **TR48A**, a university-level localization project course at Boğaziçi University, by a team of 22 members across four departments.

I served as **Project Manager Lead**, responsible for Phrase TMS setup and workflow configuration, MT pipeline development, QA automation, terminology and style guide oversight, and delivery coordination.

---

## 📁 Repository Contents

### `translation/`
Translated `.po` and `.html` files covering the full Double Commander UI and help documentation (~49,000 words total). Files were processed through Phrase TMS using MXLIFF format and post-edited by the team.

### `scripts/`
**`MT.ipynb`** — A Jupyter notebook (Google Colab) implementing an end-to-end MT pipeline using the Gemini API. 
Key features:
- Parses Phrase TMS `.mxliff` files and extracts source segments
- Dynamically injects relevant termbase entries per chunk via SUMIF-style lookup
- Embeds a condensed, LLM-optimized Turkish style guide into every prompt
- Handles API quota limits gracefully — retries with exponential backoff and prompts for a new API key on daily limit exhaustion
- Injects translations back into the MXLIFF structure and exports a ready-to-import file

### `tools/`
**`mxliff-concordance.html`** — A self-contained browser tool for searching across MXLIFF files. Drag-and-drop file loading, regex support, segment state filtering, and CSV export. No dependencies, fully local.

### `templates/`
**`tracking_sheet.xlsx`** — Project management template with anonymized dummy data. Covers budget planning, work logs per department (PM, Language Analysts, Terminologists, Eng & Testing), translation and LQA logs, testing log, and a SUMMARY sheet that auto-aggregates hours and costs via SUMIF formulas pulling from named ranges on the Rates sheet.

---

## 🛠️ Technical Stack

| Area | Tools / Technologies |
|---|---|
| TMS | Phrase TMS (MXLIFF, Translation Memory, Termbase) |
| MT | Gemini API (`gemini-2.5-flash`), Python, `google-genai` |
| File parsing | `xml.etree.ElementTree`, `pandas`, `openpyxl` |
| QA tooling | HTML, vanilla JS (no framework) |
| PM tracking | Excel / Google Sheets with named ranges and cross-sheet formulas |

---

## 🔧 Using the MT Pipeline

1. Open `scripts/MT.ipynb` in Google Colab
2. Add your Gemini API key when prompted
3. Upload your termbase (`.xlsx`) — two columns: source term, target term
4. Upload your Phrase TMS file (`.mxliff`)
5. The script processes segments in chunks of 30, injects relevant glossary terms per chunk, and downloads the translated MXLIFF on completion

> The style guide embedded in the pipeline (`CONDENSED_STYLE_GUIDE`) follows Turkish localization conventions including formal address (`Siz`), imperative UI verbs, singular nouns with numeric placeholders, and Turkish number/date formatting.

---

## 📊 Project Scope

| Metric | Value |
|---|---|
| Total word count | ~49,500 words |
| UI strings (`.po`) | ~11,800 words |
| Help documentation (`.html`) | ~37,700 words |
| Team size | 22 members |
| TMS | Phrase TMS |
| Language pair | EN → TR |
| Duration | ~4 weeks |

---

## 📝 Notes

- UI screenshots bundled with the help documentation are excluded from this repository as they are unmodified assets from the original application.
- The tracking sheet contains anonymized dummy data to demonstrate formula structure; no real team data is included.
- This project was completed for academic purposes. All translation work is original and intended as a portfolio demonstration.
