# Chain-of-Verification (CoVe) Using Generative AI

## Project Overview

Large Language Models (LLMs) can generate fluent and convincing responses but may occasionally produce factually incorrect information. This project explores the **Chain-of-Verification (CoVe)** approach to improve the reliability of factual responses through a structured, multi-step verification process.

The system is implemented using Google's Gemini API and Python. It generates an initial response, creates verification questions, answers those questions independently, and uses the resulting information to produce a final answer.

## Objectives

- Implement a multi-step Chain-of-Verification workflow.
- Explore how verification questions can help identify potential factual inconsistencies.
- Compare direct LLM answering with Chain-of-Verification.
- Evaluate generated responses using an LLM-as-a-Judge approach.
- Provide an interactive dashboard to explore the verification process and results.

## Methodology

The system follows four major stages:

1. **Initial Answer Generation:** Generate a draft response to the user's question.
2. **Verification Question Generation:** Create verification questions based on the original question and draft response.
3. **Verification Answering:** Answer the generated verification questions.
4. **Final Answer Generation:** Use the original question, draft response, verification questions, and their answers to generate a final response.

## Technology Stack

- Python
- Google Gemini API
- Google GenAI SDK
- Pandas
- Matplotlib
- Google Colab

## Evaluation

An additional experiment compares Direct Answering and Chain-of-Verification using a dataset of 8 factual questions.

Both approaches are evaluated using Gemini as an LLM judge, which classifies responses as CORRECT or INCORRECT against reference answers.

### Experimental Results

| Metric | Direct Answering | CoVe |
|---|---:|---:|
| Valid Evaluations | 7/8 | 8/8 |
| Accuracy | 100% | 100% |

Both approaches achieved 100% accuracy among their valid evaluations in this experiment. One direct-answer evaluation resulted in an error and was excluded from its accuracy calculation.

These results demonstrate the implemented workflow but do not establish that CoVe consistently outperforms direct answering.

## Interactive Dashboard

The project includes an interactive dashboard with the following sections:

- **Live CoVe:** Explore the verification workflow using custom questions.
- **Overview:** View evaluation summaries and performance metrics.
- **Explorer:** Examine individual questions and generated responses.
- **Stress Test:** Explore system behaviour using challenging questions.

## How to Run

1. Open the notebook in Google Colab.
2. Install the required dependencies.
3. Configure a Gemini API key in Google Colab Secrets using the name `GEMINI_API_KEY`.
4. Enable notebook access to the secret.
5. Execute the notebook cells in their intended order.
6. Explore the evaluation results and interactive dashboard.

## Limitations

- The additional evaluation dataset contains only 8 questions.
- The LLM-as-a-Judge approach may introduce evaluation bias.
- The evaluation results are not independently validated by human reviewers.
- The verification process does not guarantee the correction of every factual error.
- The current implementation does not retrieve evidence from external knowledge sources or documents.

## Future Scope

- Expand the evaluation dataset with more diverse and challenging questions.
- Introduce human-reviewed reference answers and independent evaluation metrics.
- Integrate external knowledge sources and retrieval-based verification.
- Explore different LLMs and verification strategies.
- Improve error handling and evaluation reliability.

## Repository Contents

- `Chain_Of_Verification.ipynb` – Complete implementation, experiments, evaluation, and interactive dashboard.

---

**Developed as a Generative AI project exploring structured verification techniques for more reliable LLM-generated responses.**
