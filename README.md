# AI-Powered-Slide-Accessibility-Tool-PPT-Alt-Text-
A Python utility for automating PowerPoint accessibility. Batch-processes images and diagrams with discipline-specific AI context for WCAG compliance.

This Python utility automates the generation of descriptive "alt-text" for images within PowerPoint presentations. It uses the **Gemini 2.5 Flash** model to analyze visual content and provide descriptions compatible with screen readers.

## Prerequisites

1. **Python 3.x**
2. **Google Gemini API Key:** Obtainable via [Google AI Studio](https://aistudio.google.com/).
3. **Required Libraries:**
```bash
pip install python-pptx google-genai python-dotenv

```
## Setup

1. Create a file named `.env` in the same directory as the script.
2. Add your API Key to the file:
```text
GOOGLE_API_KEY=your_key_here

```



## Usage

### Single File

Run the script by providing the path to a PowerPoint file. Use the `-d` flag to specify your discipline for more accurate descriptions.

```bash
python PPT_AltText.py Your_Lecture.pptx -d "Biochemistry"

```

### Batch Processing

To process an entire folder of presentations, provide the directory path. The script will process every `.pptx` file found in that folder.

```bash
python PPT_AltText.py ./Lectures_Folder -d "Biochemistry"

```

* **Input:** `FileName.pptx`
* **Output:** `FileName_Accessible.pptx` (Original files are preserved).

## How it Works

1. **Extraction:** The script scans slides for all image-based shapes.
2. **AI Analysis:** Each image is processed by the **Gemini 2.5 Flash** vision model, using the provided discipline to ensure technical context.
3. **Metadata Injection:** The generated description is written directly into the "Alternative Text" field of the image within the PowerPoint file.

## Technical Notes

* **Discipline Context:** If no discipline is provided, the script defaults to "academic research."
* **Accuracy:** Review generated text for nuances in specific diagrams, metabolic pathways, or data plots.
* **Privacy:** This script sends image data to Google's API for processing.
* **Safety:** The script automatically skips files that already have the `_Accessible` suffix to prevent redundant processing during batch runs.

---

