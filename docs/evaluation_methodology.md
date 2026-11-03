# Evaluation Methodology

## 1. Overview

An additional evaluation experiment was conducted to compare two approaches for generating factual responses using a Large Language Model:

- Direct Answering
- Chain-of-Verification (CoVe)

The objective was to examine whether introducing intermediate verification steps influences the factual correctness of generated responses.

## 2. Evaluation Dataset

A dataset containing eight factual questions was used for the experiment.

The questions covered topics such as:

- Geography
- Science
- Biology
- History
- General knowledge
- False-premise questions

Each question was associated with a reference answer used during evaluation.

Both approaches were tested using the same set of questions to maintain consistency in the comparison.

## 3. Evaluation Approaches

### A. Direct Answering

In this approach, the original question is directly submitted to the Gemini model.

The generated response is then evaluated against its corresponding reference answer.

### B. Chain-of-Verification

In this approach, the question passes through the complete CoVe workflow:

1. Generate an initial draft response.
2. Generate verification questions.
3. Answer the verification questions.
4. Generate a final response using the verification information.

The final response is evaluated against the same reference answer used for direct answering.

## 4. Evaluation Technique

An LLM-as-a-Judge approach was used to evaluate the generated responses.

The Gemini model receives the original question, reference answer, and generated response. It is instructed to classify the response as:

- **CORRECT:** The response is factually consistent with the reference answer.
- **INCORRECT:** The response contains factual inaccuracies or does not adequately match the reference answer.

Responses resulting in evaluation errors are marked separately and excluded from the accuracy calculation.

## 5. Evaluation Metric

Accuracy was used as the primary evaluation metric.

\[
Accuracy = \frac{Correct\ Evaluations}{Valid\ Evaluations} \times 100
\]

Invalid or failed evaluations are excluded from the denominator.

## 6. Experimental Results

The following results were obtained:

| Metric | Direct Answering | CoVe |
|---|---:|---:|
| Total Questions | 8 | 8 |
| Valid Evaluations | 7 | 8 |
| Correct Evaluations | 7 | 8 |
| Incorrect Evaluations | 0 | 0 |
| Accuracy | 100% | 100% |

### Interpretation

Both approaches achieved 100% accuracy among their valid evaluations.

Direct Answering had one evaluation error, resulting in seven valid evaluations, whereas CoVe had eight valid evaluations.

The experiment demonstrates that the implemented CoVe workflow successfully completed all eight evaluations. However, the results do not establish a measurable accuracy improvement over direct answering.

## 7. Limitations

The experiment has several limitations:

1. **Dataset Size:** Eight questions are insufficient to establish general performance across a wide range of factual queries.
2. **Evaluation Bias:** The same underlying model family is used for answer generation and LLM-based evaluation, potentially introducing bias.
3. **Reference-Based Evaluation:** The judge's assessment may not always capture every factual nuance or alternative valid answer.
4. **API Reliability:** Temporary API or evaluation failures can affect the number of valid observations.
5. **No External Evidence Retrieval:** The current implementation does not independently retrieve authoritative sources to verify factual claims.

## 8. Future Improvements

Future experiments could improve the evaluation process through:

- A larger and more diverse benchmark dataset.
- Human-reviewed reference answers.
- Independent evaluation using a different model or deterministic checks where applicable.
- Precision, recall, and other suitable evaluation metrics for more detailed analysis.
- Testing across multiple LLMs.
- Integration of retrieval-based verification using reliable external sources.

## 9. Conclusion

This experiment provides an initial comparison of direct LLM answering and a structured Chain-of-Verification workflow.

Although both approaches achieved the same measured accuracy on the valid evaluations, the experiment demonstrates how intermediate verification stages can be incorporated into an LLM-based application.

Larger-scale testing and independent evaluation are necessary before drawing conclusions about the general effectiveness of CoVe.
