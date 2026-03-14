# Clinical AI Evaluation Report

## Overview

This project evaluates the reliability of a clinical AI pipeline that extracts structured medical entities from OCR-processed medical charts. These systems convert unstructured clinical records into structured data that can support healthcare analytics and decision-making.

Because medical text often includes complex terminology, temporal references, and family history mentions, errors in entity extraction can lead to incorrect clinical interpretations. This project proposes a lightweight evaluation framework to assess the reliability of the extracted clinical information.

## Evaluation Approach

Each chart contains AI-generated clinical entities extracted from medical notes. The evaluation script (`test.py`) processes each chart and generates a structured report stored in the `output/` directory.

The framework evaluates the following dimensions:

* **Entity Type Error Rate** – correctness of entity classification (e.g., diagnosis, medication, procedure).
* **Assertion Error Rate** – whether a condition is correctly identified as present, absent, or uncertain.
* **Temporality Error Rate** – correct identification of current, historical, or upcoming events.
* **Subject Attribution Error Rate** – whether the condition refers to the patient or a family member.
* **Event Date Accuracy** – correctness of extracted clinical dates.
* **Attribute Completeness** – presence of required metadata fields for each entity.

All metrics are normalized between **0 and 1**.

## Quantitative Evaluation Summary

The evaluation framework processes all clinical charts in the dataset and generates structured evaluation reports for each chart. These reports provide quantitative measurements of extraction reliability across entity classification, assertion detection, temporal reasoning, subject attribution, and metadata completeness.

By analyzing these metrics across multiple charts, the framework helps identify patterns in system performance and highlights areas where the AI pipeline may require additional validation or reliability checks.

## Error Heat-Map (Conceptual)

Based on the evaluation framework, certain reasoning dimensions tend to be more error-prone in clinical entity extraction systems:

* Temporality interpretation (distinguishing past vs current events)
* Subject attribution (patient vs family history mentions)
* Entity classification when medical terms belong to multiple categories

These areas represent higher-risk points in the extraction pipeline and are important targets for reliability improvements.

## Observed Challenges

Clinical NLP systems commonly face several reliability challenges:

* Misclassification of entity types.
* Incorrect temporal interpretation of medical events.
* Confusion between patient conditions and family history.
* Missing metadata attributes in extracted entities.

## Proposed Reliability Guardrails

To improve the robustness of the pipeline, the following safeguards are recommended:

1. Rule-based checks for family history detection.
2. Temporal validation for clinical events.
3. Attribute completeness verification before downstream processing.
4. Optional secondary validation using LLM-based reasoning.

## Conclusion

This evaluation framework provides a structured approach for assessing the reliability of clinical AI extraction systems. By analyzing entity classification, temporal reasoning, subject attribution, and metadata completeness, it helps identify potential weaknesses and supports the development of more trustworthy healthcare AI systems.
