# Swiggy Customer Review Analysis

## Project Overview

This project analyzes customer reviews from the Swiggy app using Python and Generative AI.

The main objectives are:

- Clean and prepare customer review data using Pandas.
- Identify critical customer reviews based on ratings.
- Find common complaint keywords using rule-based text analysis.
- Select highly detailed negative reviews.
- Generate personalized and empathetic customer support emails using Google Gemini.

## Dataset

The dataset used in this project is a Swiggy customer review dataset.

Main columns used:

- `review_description` — Customer review text
- `rating` — Customer rating from 1 to 5
- `clean_review` — Cleaned review text

The dataset contains **200,791 customer reviews**.

## Data Cleaning

The following cleaning steps were performed:

1. Converted customer review text to lowercase.
2. Removed punctuation and special characters using regular expressions.
3. Removed extra whitespace.
4. Created a new `clean_review` column.
5. Preserved the original `review_description` column.
6. Missing metadata fields were handled where required for the analysis.

## Rule-Based Filtering & Insights

Critical reviews were identified using a simple rule:

> **Rating 1 or 2 = Critical Review**

Calculated results:

- **Total Reviews:** 200,791
- **Critical Reviews:** 110,949
- **Critical Review Percentage:** 55.26%
- **Average Rating:** 2.67 / 5

Common complaint keywords were identified using Python's `Counter` after removing common stopwords.

Top complaint keywords:

| Keyword | Frequency |
|---|---:|
| order | 53,357 |
| delivery | 46,035 |
| food | 33,881 |
| customer | 27,605 |
| worst | 27,287 |
| service | 22,189 |
| time | 21,598 |
| bad | 17,437 |
| ordered | 12,602 |
| money | 10,878 |

These keywords indicate that major customer concerns are related to orders, delivery, food quality/service, delays, and money-related issues.

## Generative AI Outreach

Three highly detailed critical reviews were selected from the 1–2 star reviews based on review length.

Google Gemini was used to generate personalized and empathetic apology emails for the selected reviews.

### Model Used

`gemini-3.5-flash`

The prompt instructed Gemini to:

- Address the customer's specific complaints.
- Apologize sincerely and show empathy.
- Use only information supported by the customer review.
- Avoid inventing facts.
- Avoid unsupported refund, coupon, or compensation promises.
- Keep the email around 150–200 words.
- End with `Sincerely, Customer Support Team`.

The three completed Gemini-generated emails are included in the notebook's **Final Output** section.

## Project Structure

```text
Swiggy Customer Review Analysis/
│
├── swiggy_feedback_GEMINI_FINAL.ipynb
├── swiggy.csv
└── README.md
```

## How to Run

1. Keep `swiggy.csv` in the same folder as the notebook.
2. Open `swiggy_feedback_GEMINI_FINAL.ipynb` in Jupyter Notebook or JupyterLab.
3. Run the data loading and analysis cells in order.
4. Run the Gemini setup cells in Section 6.
5. When prompted, enter your Gemini API key securely.
6. Run the Gemini email-generation function if you want to regenerate the emails.
7. Review the completed three emails in the **Final Output** section.

## API Key Setup

The notebook uses `getpass` so the Gemini API key is not written directly into the notebook.

Example:

```python
import os
from getpass import getpass

os.environ["GEMINI_API_KEY"] = getpass("Enter your Gemini API key: ")

## NOTE: 
This project uses the Google Gemini API for generating personalized customer apology emails.

For security reasons, the API key is not included in this repository.

Before running the notebook, enter your own Gemini API key when prompted.
```

### Security

- Do not paste your API key into publicly shared code.
- Do not commit the API key to GitHub.
- If an API key is accidentally exposed, revoke it and create a new one.

## Requirements

The notebook uses Python and the following main libraries:

- pandas
- numpy
- re
- collections
- google-genai

The Gemini SDK can be installed with:

```bash
pip install -U google-genai
```

## API Key Setup

This project uses the Google Gemini API for generating personalized customer apology emails.

For security reasons, the API key is not included in this repository.

Before running the notebook, enter your own Gemini API key when prompted.
