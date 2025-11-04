# PDF Summarizer App

A lightweight, **offline-capable** web application that lets you **upload PDF documents** and **generate concise summaries** using state-of-the-art transformer models from **Hugging Face**—all in your browser. Built with **Streamlit**, this tool is perfect for quickly distilling long reports, research papers, or articles without sending your data to the cloud.

---

## ✨ Key Features

- **PDF Text Extraction**: Upload any `.pdf` file and extract its full text content.
- **Intelligent Chunking**: Automatically splits long documents into manageable chunks to respect model token limits.
- **Transformer-Based Summarization**: Uses pretrained models like `facebook/bart-large-cnn` (or faster alternatives).
- **Fully Offline After Setup**: Once models are downloaded, no internet connection is needed.
- **User-Friendly UI**: Clean, responsive interface powered by Streamlit.
- **Optimized for Large PDFs**: Handles multi-page documents with efficient chunk processing.

---

## 🛠️ Requirements

- **Python 3.8 or higher**
- **pip** (Python package manager)
- (Optional but recommended) Virtual environment (`venv`)

---

## 📦 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/lekshmi-c/pdf-summarizer.git
cd pdf-summarizer
```

### 2. Set Up a Virtual Environment
```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

> This installs:
> - `streamlit` (web UI)
> - `transformers` & `torch` (Hugging Face models)
> - `PyMuPDF` (PDF text extraction)

---

## ▶️ Run the Application

```bash
streamlit run app.py
```

Open your browser and go to:  
👉 **http://localhost:8501**

---

## ⚙️ Optional Configuration

To avoid file watcher conflicts between **Streamlit** and **PyTorch**, create a `.streamlit/config.toml` file:

```toml
[server]
fileWatcherType = "none"
```

Place it in your project root:
```
pdf-summarizer/
└── .streamlit/
    └── config.toml
```

---

## 🧪 How to Use

1. **Launch** the app with `streamlit run app.py`.
2. **Upload** a `.pdf` file using the file uploader.
3. The app will:
   - Extract text from all pages,
   - Split it into chunks (if too long),
   - Summarize each chunk using the transformer model,
   - Combine and display the final summary.
4. View the **condensed summary** directly in your browser.

---

## 🧠 Model Options

- **Default**: `facebook/bart-large-cnn` (high quality)
- **Faster alternative**: `sshleifer/distilbart-cnn-12-6` (smaller, quicker)

To switch models, modify the model name in `app.py`:
```python
summarizer = pipeline("summarization", model="sshleifer/distilbart-cnn-12-6")
```

> 💡 **Note**: The model is **cached after the first run**, so subsequent summaries load faster.

---

## ⚠️ Known Issues & Notes

- **PyTorch + Streamlit Conflict**: Solved by disabling Streamlit’s file watcher via `config.toml`.
- **Performance on CPU**: Summarization may be slow for large PDFs if running on CPU; consider using a smaller model for faster results.
- **Token Limits**: Very long documents are split automatically, but extremely dense technical text may lose nuance.

---

## 🗂️ Project Structure

```
pdf-summarizer/
├── app.py                  # Main Streamlit application
├── requirements.txt        # Python dependencies
└── .streamlit/
    └── config.toml         # Streamlit server config (optional)
```

---

## 📄 License

This project is open-source. See the repository for license details.

---

> 💡 **Tip**: Great for students, researchers, or professionals who need to quickly grasp the essence of long documents—without compromising privacy or requiring an internet connection after setup!
