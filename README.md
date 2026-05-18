# 👁️ Tamil OCR Pro (Client-Side)

A production-grade, 100% client-side Optical Character Recognition (OCR) web application optimized for Tamil and English text. Built entirely in a single HTML file, it requires absolutely no backend, ensuring complete user privacy and zero server costs.

## ✨ Features

* **🔒 100% Private & Serverless:** Images are processed entirely in the browser's memory using WebAssembly. No data is ever uploaded to a server.
* **📏 Pixel-Perfect Paragraph Reconstruction:** Bypasses standard Tesseract Page Segmentation errors by physically measuring bounding box `y`-coordinates to perfectly reconstruct line spacing and paragraph stanzas.
* **🪄 Live "Enhance Scan" Mode:** Integrates `OpenCV.js` to provide a live visual preview of advanced image cleanup (Median Blur + Gaussian Adaptive Thresholding) for shadowed or low-quality documents.
* **⚡ Hybrid Preprocessing:** Uses a lightning-fast native JavaScript Canvas thresholding engine for clean images, keeping processing times near-instant.
* **🧹 ZWNJ Ghost-Character Stripping:** Automatically filters out invisible Unicode artifacts (Zero-Width Non-Joiners) that commonly corrupt Tamil OCR output when pasting into text editors.
* **📱 Modern SaaS UI:** Responsive, mobile-first design with drag-and-drop, paste-to-upload, and real-time extraction progress indicators.

## 🛠️ How It Works (The Tech Stack)

This tool combines the power of two WebAssembly (WASM) engines, orchestrated by Vanilla JavaScript:

1. **Tesseract.js (v5):** The core AI engine. It utilizes an LSTM (Long Short-Term Memory) neural network to recognize characters. We use `tessedit_pageseg_mode: 6` to force strict line-by-line reading, paired with our custom bounding-box math for accurate spacing.
2. **OpenCV.js:** Used for the "Enhance Scan" feature. It applies a mathematical pipeline (`cv.cvtColor` -> `cv.medianBlur` -> `cv.adaptiveThreshold`) to isolate text from noisy backgrounds, shadows, and paper textures.
3. **Vanilla JS & Canvas API:** Handles the lightweight fallback preprocessing, UI state management, and file decoding (supporting JPG, PNG, WEBP, GIF).

## 🚀 Getting Started

Since this is a client-side tool, there is no build step or server required!
1. Clone this repository or download the `index.html` file.
2. Open `index.html` directly in any modern web browser (Chrome, Firefox, Safari, Edge).
3. Drag and drop an image to start extracting.

## 🗺️ Future Roadmap (Contributions Welcome!)

While Version 1 is highly optimized for printed text and standard images, here are potential pipelines for future versions:

* **[ ] Cloud API Backend (Option B):** Add a toggle to route complex images (like heavy handwriting) to a Python/FastAPI backend running state-of-the-art models like **EasyOCR** or **PaddleOCR**.
* **[ ] Document Parsing:** Integrate `pdf.js` to allow users to upload multi-page PDFs, converting them to canvas images for batch OCR processing.
* **[ ] Auto-Deskewing:** Implement a Hough Line Transform in OpenCV to automatically detect and rotate skewed/crooked images before passing them to Tesseract.
* **[ ] Multi-Language Expansion:** Add a dynamic UI to fetch and cache other `.traineddata` language models from the Tesseract CDN.

## 📄 License
MIT License - Free to use, modify, and distribute.
