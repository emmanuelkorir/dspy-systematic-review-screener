# DSPy Systematic Review Screener

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/dspy-systematic-review-screener/blob/main/dspy-systematic-review-screener.ipynb)

An AI-powered pipeline using the DSPy framework to automate the title and abstract screening phase of systematic reviews and meta-analyses. This project is designed to be run entirely within Google Colab.

## Features

-   **Structured AI Reasoning:** Uses `dspy.ChainOfThought` 
-   **Ensemble Voting:** Employs a voting system (e.g., 3 "voters") to increase the reliability and confidence of each screening decision.
-   **Model Agnostic:** Built with `LiteLLM` 
-   **Optimized Prompts:** Leverages `dspy.BootstrapFewShot` to "teach" the model the screening task using a few high-quality examples, creating an optimized prompt.
-   **Rate-Limit Safe** 

## Technology Stack

-   **Framework:** [DSPy](https://dspy.ai/)
-   **LLM Adapter:** [LiteLLM](https://www.litellm.ai/)
-   **Backend Models:** Can be configured for Google Gemini, OpenAI GPT-4/3.5, Anthropic Claude, and 100+ others.
-   **Data Handling:** [Pandas](https://pandas.pydata.org/docs/user_guide/10min.html)

## Setup and Usage

Follow these steps to run the screening pipeline for your own research.

### 1. Open in Google Colab

Click the "Open in Colab" badge at the top of this README, or use the link below:

**[https://colab.research.google.com/github/YOUR_USERNAME/dspy-systematic-review-screener/blob/main/dspy_review_screener.ipynb](https://colab.research.google.com/github/YOUR_USERNAME/dspy-systematic-review-screener/blob/main/dspy_review_screener.ipynb)**

**Important:** Replace `YOUR_USERNAME` in the link above with your actual GitHub username!

### 2. Set Up Your API Key

The notebook uses Colab's built-in Secrets manager for security. You will need an API key from an LLM provider (like Google AI Studio).

1.  In the Colab notebook, click the **key icon (🔑)** in the left sidebar.
2.  Click **"Add a new secret"**.
3.  For the **Name**, enter `GOOGLE_API_KEY`.
4.  For the **Value**, paste your API key.
5.  Make sure the **"Notebook access"** toggle is turned on.

### 3. Customize for Your Protocol

The notebook is pre-configured for a sample systematic review. To adapt it for your own project, edit the code cells containing:

-   **`inclusion_criteria`:** Update this string with your study's eligibility criteria.
-   **`exclusion_criteria`:** Update this string with your exclusion rules.
-   **`train_examples`:** **This is the most important step.** Replace the existing examples with 2-3 high-quality examples specific to *your* research question. This teaches the AI how to reason correctly for your study.

### 4. Run the Notebook

1.  Go to **Runtime -> Run all** in the Colab menu.
2.  The notebook will first install the required libraries and restart the session.
3.  Then, it will configure the model and prompt you to **upload your articles CSV file**. Your CSV must contain `title` and `abstract` columns.
4.  The screening process will begin, showing a progress bar.
5.  When finished, the results will be displayed in a table and saved as a CSV file that you can download from the Colab file pane.
