# BITS Academic Course Recommender

**Postman Round 2 Submission | BITS Pilani**

A Google Colab–based academic course recommender with an interactive **Gradio dashboard**. It uses supplied BITS academic documents and a student profile to identify academic requirements, filter courses, and recommend options that match natural-language preferences.

> **Scope:** Core Tasks 1–7 and implementation guidance for Tasks 9–10. Optional **Task 8 (Timetable Intelligence)** is excluded. Recommendations are advisory; incomplete prerequisite or restriction data is marked as needing verification, not assumed eligible.

## Features

- Create and update a student profile: campus, admission year, degree/dual degree, semester, completed and current courses, minor, and interests.
- Analyse outstanding **CDC, DEL, HUEL and OPEL** requirements where supported by the supplied data.
- Apply documented academic rules and known restrictions before matching preferences.
- Interpret queries such as *“Suggest AI-related DELs”*, *“Find an OPEL with no attendance requirement”*, and *“Suggest courses without a midsem.”*
- Retrieve course and handout information from structured records, with source references and explicit uncertainty for unverifiable properties.
- Display live results through a Gradio dashboard.

## Repository Files

```text
BITS-Academic-Course-Recommender/
├── 01_FINAL_SUBMISSION.ipynb   # Colab notebook
├── DATASET_LINK.pdf            # Google Drive link to the data ZIP
└── README.md                   # This document
```

**Important:** The full source archive is hosted on Google Drive because it contains many PDFs. Open `DATASET_LINK.pdf` to obtain its download link. The notebook and linked archive together provide the runnable project. For reviewers seeking standalone source modules in GitHub, those are also inside the linked repository archive.

## Dataset

The supplied materials include:

- **BITS Academic Regulations (2023)**
- **BITS Bulletin (2025–26)**
- **Pilani campus timetable, First Semester 2026–27**
- **540 course handout PDFs**
- **Structured/preprocessed academic data** used by the recommender

Source documents are the primary authority. If the documents do not establish a prerequisite, course category, or handout property reliably, the application should present that information as **unverified**.

## Running in Google Colab

1. Download `01_FINAL_SUBMISSION.ipynb` from this repository.
2. Open [Google Colab](https://colab.research.google.com/) and upload the notebook.
3. Open `DATASET_LINK.pdf`, follow its Google Drive link, and download the **complete ZIP archive**. Do **not** extract or rename the ZIP before uploading unless the notebook explicitly directs you to.
4. In Colab, select **Runtime → Run all**.
5. When prompted, upload the complete ZIP archive.
6. Allow the notebook to install dependencies, prepare the data, and run its checks.
7. Open the **Gradio dashboard URL** printed by the notebook and enter a student profile and query.

A Google Colab runtime, internet access for package installation, and enough space for ZIP extraction are required. Any optional LLM/API integration requires its own credentials; the core recommendation flow does not require you to publish an API key.

## Recommendation Pipeline

```text
Student Profile + Natural-Language Query
                   ↓
      Academic Requirement Analysis
                   ↓
        Remaining CDC/DEL/HUEL/OPEL
                   ↓
             Eligibility Filter
                   ↓
            Preference Matching
                   ↓
           Academic Validation
                   ↓
       Explained Recommendations
```

The data is preprocessed into structured records before retrieval. Deterministic checks are preferred for academic rules; language processing supports intent interpretation and matching, rather than inventing eligibility rules. The dataset includes references that allow extracted facts to be traced to their sources.

## Validation and Known Limitations

Local development checks included notebook execution, recommendation regression tests, and a dashboard startup check. **These do not guarantee that Colab sharing, Google Drive permissions, or every external prerequisite can be verified in another environment.** Reviewers should rerun the notebook with the linked data archive.

- **Task 8 timetable intelligence is intentionally not implemented.** The timetable is supplied as source material but clash-free schedule selection is not claimed.
- Some current, programme-specific prerequisites and exceptions may require confirmation from official BITS academic resources.
- This tool is intended to assist course exploration, **not replace official registration approval**.

## Sources

BITS Pilani Academic Regulations (2023); Bulletin (2025–26); First Semester 2026–27 Timetable; provided course handouts. Source files are accessible through the Drive archive linked in `DATASET_LINK.pdf`.
