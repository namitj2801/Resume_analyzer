# Resume Analyzer using NLP

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A powerful tool to automate the screening of resumes by leveraging Natural Language Processing (NLP) to parse, analyze, and rank candidates based on a job description.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [How It Works](#how-it-works)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The Resume Analyzer is designed to streamline the initial stages of the recruitment process. It takes a collection of resumes (in `.pdf` or `.docx` format) and a job description as input. Using NLP techniques, it extracts key information like skills, experience, and contact details from each resume. It then calculates a relevance score for each candidate by comparing their resume against the job description, helping recruiters to quickly identify the most promising applicants.

## Features

- **Multi-Format Resume Parsing:** Supports both PDF (`.pdf`) and Microsoft Word (`.docx`) files.
- **Key Information Extraction:** Automatically extracts crucial details:
  - Candidate's Name
  - Contact Information (Email, Phone)
  - Skills
  - Work Experience
  - Education
- **Job Description Matching:** Intelligently compares the content of a resume with a given job description.
- **Candidate Scoring & Ranking:** Ranks candidates based on a cosine similarity score, providing a quantitative measure of their fit for the role.
- **Simple Web Interface:** An intuitive web UI to upload resumes, input a job description, and view the analyzed results.

## How It Works

The analysis pipeline involves several NLP stages:

1.  **Text Extraction:** The system first reads and extracts raw text from the uploaded resume files.
2.  **Text Preprocessing:** The extracted text is cleaned by removing stop words, punctuation, and special characters. It is then tokenized and lemmatized to create a clean corpus for analysis.
3.  **Named Entity Recognition (NER):** A pre-trained `spaCy` model is used to identify and extract entities like `PERSON` (for the candidate's name), email addresses, and phone numbers.
4.  **Section Segmentation:** The resume is segmented into logical sections like "Education," "Work Experience," and "Skills" using rule-based pattern matching on common resume headings.
5.  **Skill Extraction:** A predefined list of technical and soft skills is used to scan the text and identify the candidate's competencies.
6.  **Similarity Scoring:** The text from the resume and the job description are converted into numerical vectors using TF-IDF (Term Frequency-Inverse Document Frequency). Cosine similarity is then calculated between these vectors to determine the match score. A higher score indicates a better match.

## Tech Stack

- **Backend:** Python, Flask
- **NLP Libraries:** spaCy, NLTK
- **File Parsing:** `PyPDF2`, `python-docx`
- **Machine Learning:** Scikit-learn (for TF-IDF and Cosine Similarity)
- **Frontend:** HTML, CSS (Bootstrap)

## Installation

Follow these steps to get the project running on your local machine.

**Prerequisites:**
- Python 3.8+
- `pip` package manager

**1. Clone the repository:**
```bash
git clone https://github.com/your-username/resume-analyzer.git
cd resume-analyzer
```
*(Replace `your-username` with your actual GitHub username)*

**2. Create and activate a virtual environment:**

*On macOS/Linux:*
```bash
python3 -m venv venv
source venv/bin/activate
```

*On Windows:*
```bash
python -m venv venv
.\venv\Scripts\activate
```

**3. Install dependencies:**
*(Ensure you have a `requirements.txt` file in your project root)*
```bash
pip install -r requirements.txt
```

**4. Download necessary NLP models:**
```bash
python -m spacy download en_core_web_sm
python -m nltk.downloader punkt stopwords wordnet
```

**5. Run the application:**
```bash
flask run
```
The application will be available at `http://127.0.0.1:5000`.

## Usage

1.  Open your web browser and navigate to `http://127.0.0.1:5000`.
2.  Paste the job description into the large text area.
3.  Click "Choose Files" to select one or more resume files (`.pdf` or `.docx`).
4.  Click the "Analyze Resumes" button to start the process.
5.  The results will be displayed in a table, showing the extracted information and the match score for each resume, sorted from highest to lowest score.

## Project Structure

```
resume-analyzer/
├── app.py              # Main Flask application file
├── resume_parser.py    # Core NLP and parsing logic
├── requirements.txt    # Project dependencies
├── static/             # Static files (CSS, JS)
└── templates/          # HTML templates for the web UI
```

## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**. Please refer to the `CONTRIBUTING.md` file for details.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more information.

