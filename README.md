AI-Powered Slide Accessibility Tool (PPT-Alt-Text)

This utility automates the generation of descriptive "alt-text" for images in PowerPoint presentations. It uses the Gemini 2.5 Flash model to analyze visual content and provide descriptions compatible with screen readers.

Unlike standard accessibility tools, this script uses a recursive deep-scan to identify and tag images that are:

Copy-Pasted: Standardizes images that PowerPoint "containerizes" during direct paste operations.

Nested in Groups: Drills down into grouped objects, common in chemical structures and complex diagrams.

Layout Placeholders: Captures images dragged into pre-set university template boxes.

Prerequisites
Python 3.x

Google Gemini API Key: Obtainable via Google AI Studio.

Required Libraries:

Bash
pip install python-pptx google-genai python-dotenv
Installation & Setup
Clone the Repository:

Bash
git clone https://github.com/walternmoss/PPT_Alt-Text.git
cd PPT_Alt-Text
Configure Environment: Create a file named .env in the root directory and add your API Key:

Plaintext
GOOGLE_API_KEY=your_key_here
Local Safety: The .gitignore file is pre-configured to ensure your .env (API Key) is never uploaded to GitHub.

Usage
⚠️ Important: Safety First

It is highly recommended to work on copies of your files. While the script creates a new file with an _Accessible suffix, maintaining an untouched original is best practice to prevent any accidental data loss.

Single File

Run the script by providing the path to a PowerPoint file. Use the -d flag to specify your discipline (e.g., Biochemistry, History) for technical accuracy.

Bash
python PPT_AltText.py Your_Lecture.pptx -d "Biochemistry"
Batch Processing

To process an entire folder of presentations, provide the directory path:

Bash
python PPT_AltText.py ./Lectures_Folder -d "Biochemistry"
Output: Generates a new file with the suffix _Accessible.pptx.

UI Visibility: The script writes to three separate internal XML locations (name, description, and the descr attribute) to ensure descriptions appear correctly in the PowerPoint Accessibility Pane.

Technical Notes
API Credits & Quotas: This tool uses the Gemini API. If you are using a free tier, you may hit rate limits during large batch jobs. If you have a paid tier, processing hundreds of high-resolution images across many decks will consume credits. Monitor your Google AI Studio console to track usage and costs.

Privacy: This script sends image data to Google's API for processing. Avoid using it with slides containing sensitive student data.

Verification: While highly accurate, always review descriptions of complex metabolic pathways or specific data plots.

Lock Files: Ensure PowerPoint is closed before running the script. The tool needs to modify the internal XML; if PowerPoint is open, it creates a "lock file" (starting with ~$) that can cause the script to fail.
