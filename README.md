# AI-Powered Slide Accessibility Tool (PPT-Alt-Text)

This utility automates the generation of descriptive "alt-text" for images in PowerPoint presentations. It uses the **Gemini 2.5 Flash** model to analyze visual content and provide descriptions compatible with screen readers.

Unlike standard accessibility tools, this script uses a **recursive deep-scan** to identify and tag images that are:

* **Copy-Pasted:** Standardizes images that PowerPoint "containerizes" during direct paste operations.
* **Nested in Groups:** Drills down into grouped objects, common in chemical structures and complex diagrams.
* **Layout Placeholders:** Captures images dragged into pre-set university template boxes.

## Prerequisites

1. **Python 3.x**
2. **Google Gemini API Key:** Obtainable via [Google AI Studio](https://aistudio.google.com/).
3. **Required Libraries:**
```bash
pip install python-pptx google-genai python-dotenv

```



## Installation & Setup

1. **Clone the Repository:**
```bash
git clone https://github.com/walternmoss/PPT_Alt-Text.git
cd PPT_Alt-Text

```


2. **Configure Environment:** Create a file named `.env` in the root directory and add your API Key:
```text
GOOGLE_API_KEY=your_key_here

```


3. **Local Safety:** The `.gitignore` file is pre-configured to ensure your `.env` (API Key) is never uploaded to GitHub.

## Usage

### Single File

Run the script by providing the path to a PowerPoint file. Use the `-d` flag to specify your discipline (e.g., Biochemistry, History) for technical accuracy.

```bash
python PPT_AltText.py Your_Lecture.pptx -d "Biochemistry"

```

### Batch Processing

To process an entire folder of presentations, provide the directory path:

```bash
python PPT_AltText.py ./Lectures_Folder -d "Biochemistry"

```

* **Output:** Generates a new file with the suffix `_Accessible.pptx`.
* **UI Visibility:** The script writes to three separate internal XML locations (`name`, `description`, and the `descr` attribute) to ensure descriptions appear correctly in the PowerPoint **Accessibility Pane**.

## Technical Notes

* **Privacy:** This script sends image data to Google's API for processing. Avoid using it with slides containing sensitive student data.
* **Verification:** While highly accurate, always review descriptions of complex metabolic pathways or specific data plots.
* **Lock Files:** Ensure PowerPoint is closed before running the script to avoid "temporary file" errors.

---
