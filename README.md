# 📚 Book Forge

**PDF → EPUB & A5 PDF converter** — Python. No Calibre required..

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Flask](https://img.shields.io/badge/Flask-3.0-green)
![License](https://img.shields.io/badge/license-MIT-orange)

---

## ✨ Features

- 🔍 **Automatic OCR** — Converts scanned pages to text (mixed Turkish and English).
- 📖 **EPUB** — Smooth format for phones, tablets, and e-readers.
- 📄 **A5 PDF** — Novel-sized, easy to read.
- 🎛️ **Browser interface** — Drag-and-drop, live log
- ⚡ **Advanced PDF** — Pages containing text automatically skip OCR.
- 🐍 **Python** — Calibre installation is not required.

---

## 📦 Libraries Used

| Duty | Library |
|---|---|
| OCR | `ocrmypdf` + Tesseract |
| PDF reading | `pymupdf` (fitz) |
| Creating an EPUB | `ebooklib` |
| Creating an A5 PDF | `reportlab` |
| Web interface | `flask` |

---

## 🛠️ Installation

### 1. Install Tesseract (system application, once)

**Windows:**
→ https://github.com/UB-Mannheim/tesseract/wiki
In the installation, select "Additional language data" → Turkish

**macOS:**
```bash
brew install tesseract tesseract-lang
```

**Linux (Debian/Ubuntu):**
```bash
sudo apt install tesseract-ocr tesseract-ocr-tur tesseract-ocr-eng
```

### 2. Install Python dependencies

```bash
pip install -r requirements.txt
```

### 3. Run

```bash
python app.py
```

Open in browser: **http://localhost:5000**

---

## 🚀 Usage

1. Drag and drop PDF or select PDF
2. Enter book name (optional)
3. Select language → Select output format
4. Turn OCR on/off
5. **Convert** → Download

---

## 📂 Project Structure

```
bookforge/
├── app.py           # Flask server
├── converter.py     # PDF → EPUB / A5 PDF pipeline
├── templates/
│   └── index.html   # Interface
├── uploads/         # Temporary uploads (git'e girmez)
├── output/          # Outputs (git'e girmez)
├── requirements.txt
└── README.md
```

---

## ⚙️ Pipeline

```
PDF Input
  │
  ├─► ocrmypdf     → Convert scanned pages to text (skips pages with text)
  │
  ├─► pymupdf      → Extract text page by page
  │
  ├─► Bölüm tespiti → Detect chapters from title lines
  │
  ├─► ebooklib     → Create EPUB
  │
  └─► reportlab    → Create A5 PDF (Georgia, justify, 10.5pt)
```

---

## 🔧 Troubleshooting

**Tesseract not found:**
Is `tesseract --version` working? On Windows, it must be added to PATH.

**OCR quality is low:**
Turkish language pack must be installed. If not selected during installation, install again.

**EPUB is empty:**
The PDF may be completely visual (scanned) — leave OCR on.

---

## 📄 License

MIT License
