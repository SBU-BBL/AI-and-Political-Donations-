# POL 487: Leveraging Generative AI to Clean & Analyze Political Contribution Data

Welcome to the official repository for our Spring 2025 research project under Professor Danling Jiang at Stony Brook University. This project uses **Python**, **Google Colab**, and **Generative AI** tools to clean, match, and analyze Federal Election Commission (FEC) data with corporate executive datasets to study patterns in political donations.

## Project Summary

Our goal is to:
- **Match political donations** from FEC records to top executives of public companies.
- Use **AI and NLP** to enhance matching quality, disambiguate contributor names (e.g., "Bill Gates" vs. "William Gates"), and assign political alignment ratings based on public data.
- Build a scalable tool for future researchers, journalists, or watchdog groups.

## 📂 Project Structure

```
├── colab_employer_matcher.ipynb              # Python-based fuzzy matching and cleaning tool
├── Colab_Employer_Matcher_Instructions.pdf   # Step-by-step guide to running the notebook
├── POL 487 (API Notes).pdf                   # Overview of FEC API use, endpoints, scraping
├── POL 487 (Name Searching Code).pdf         # Code for programmatic filtering and file handling
├── POL 487 Useful Prompt.pdf                 # Early AI prompt for organizing contribution data
├── ✅ Refined Prompt.pdf                      # Final prompt used for AI-generated political lean ratings
├── POL 487 – (For Github).pdf                # Central links and documentation references
└── Readme.md                                 # You're here!
```

## Core Components

### 1. Employer Matching Tool (Colab Notebook)
We developed a Google Colab notebook using `pandas`, `fuzzywuzzy`, and `regex` to:
- Clean employer names (remove suffixes like "Inc", "LLC")
- Perform fuzzy string matching between donor employer fields and executive company names
- Output scores and flags for review  
**Threshold: `match_score >= 90` is considered a match**

See `Colab_Employer_Matcher_Instructions.pdf` for a complete walkthrough.

### 2. FEC Data Integration via API
Using the FEC public API:
- We collect and update campaign contribution data
- API endpoints like `/schedules/schedule_a/` were used to pull individual donor records
- Authentication via API key allowed scalable access (1,000+ calls/hour)

API guidance and wrapper setup: `POL 487 (API Notes).pdf`

### 3. Political Alignment Rating via Generative AI
After cleaning and matching, we used AI prompts to evaluate political leanings of matched executives.  
The **Refined Prompt** asks AI to assign a **1–10 rating** based on:
- Donation patterns
- Public stances
- Interview comments  
*1 = Strong Democrat, 10 = Strong Republican*

See: `✅ Refined Prompt.pdf`

## Development Notes

### Challenges Encountered
- AI hallucination during early matching tasks
- Name disambiguation (e.g., “Bill” vs. “William”) — resolved using fuzzy matching & code-based logic
- Data formatting inconsistencies between FEC and executive files

### Key Improvements
- Transitioned from prompt-based name matching to **code-based entity resolution**
- Developed scalable filters for matching and rating across large datasets
- Combined CSV processing with AI interpretation

## Useful Links

- [FEC API Developer Portal](https://api.open.fec.gov/developers/)
- [FEC Data Download (Bulk)](https://www.fec.gov/data/browse-data/?tab=bulk-data)
- [Swagger API Schema Explorer](https://api.open.fec.gov/swagger/)
- [Jupyter Notebook (Try It Online)](https://jupyter.org/try-jupyter/notebooks/?path=Untitled.ipynb)

## Getting Started

To run the notebook:

1. Open `colab_employer_matcher.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Upload your CSVs when prompted
3. Run each cell sequentially (Shift + Enter)
4. Output: `matched_output.csv` with `match_score` and `match_status` fields

To evaluate political leanings:

- Use the **Refined Prompt** in any Gen AI platform (ChatGPT, Claude, etc.)
- Provide public executive details + ask for rating + short justification

## Future Plans

- Train custom LLMs for name disambiguation and donation pattern recognition
- Integrate AI-based anomaly detection
- Build interactive dashboards for contribution transparency

## Acknowledgments

- Project Lead: **William Draney**
- Supervised by: **Professor Danling Jiang**
- Contributors: Zoe, Dana, Raymond  
Course: **POL 487 – Research in Political Science, Spring 2025**
