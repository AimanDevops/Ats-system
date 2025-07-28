# ATS Resume Evaluator using Gemini 2.0 & LangChain

This is an AI-powered tool built on **Google Gemini 2.0 Flash** and **LangChain** to evaluate resumes (in PDF format) against a custom job description. It simulates an **HR review** and an **Applicant Tracking System (ATS)** to assess match percentage, identify missing keywords, and rank candidates accordingly.

---

## Features

- Upload and evaluate **single or multiple resumes**
- Converts **PDF resumes** into images and sends them to Gemini 2.0 for analysis
- Calculates **match percentage**, **missing keywords**, and provides **HR feedback**
- Ranks all resumes based on their suitability for the given job description

---

## Requirements

Make sure you're running this in **Google Colab**. The script installs these dependencies:

```bash
!apt-get -q install poppler-utils
!pip install -q pdf2image langchain langchain-core langchain-community langchain-google-genai
```

Also, set your **Gemini API Key**:

```python
GOOGLE_API_KEY = "your_actual_key_here"
os.environ["GOOGLE_API_KEY"] = GOOGLE_API_KEY
```

---

## Files & Code Structure

```bash
├── ats_resume_evaluator.ipynb   # Main Colab notebook script
├── README.md                    # This file
```

---

## How It Works

1. **Upload PDF Resumes**: Choose one or more resumes from your local machine.
2. **Enter Job Description**: Provide a detailed job description in plain text.
3. **Evaluation**:
   - For each resume:
     - It converts the first page to a base64 image
     - Sends it with the job description to Gemini 2.0
     - Parses response for match %, missing keywords, and evaluation
4. **Ranking**:
   - Resumes are ranked in descending order of match percentage.

---

## Output Format (Example)

```text
Ranked Resume Matches:

Rank 1: resume_A.pdf
Match: 92%
Missing Keywords: Kubernetes, REST APIs
Evaluation: Strong experience in Python and ML, but lacks backend deployment skills.

Rank 2: resume_B.pdf
Match: 76%
Missing Keywords: Docker, SQL
Evaluation: Good frontend skills, moderate ML experience, missing core DevOps tools.
```

---

## Prompt Templates

Two prompt modes are supported:
- `"HR Review"`: Human-like feedback from an HR expert
- `"Match Percentage"`: Strict ATS-style evaluation with numerical score

---

## Known Issues

- Gemini API quota might get exhausted (Error 429). Consider applying for higher quota or retry after a minute.
- Only the **first page** of each resume is used for evaluation.
- PDFs with low-quality scans might result in inaccurate evaluations.

---

## Security Note

Do **NOT** upload your API key to public GitHub repositories. Use `.env` or Colab secrets when deploying for real use.

---
