# Datasets Are All You Need

**Can an LLM teach itself how to prompt just by looking at a dataset?**

_Spoiler alert: it sure can 😉_

This sample demonstrates how a Large Language Model (LLM), specifically Gemini 2.5 Flash, can iteratively refine a prompt to transform input data into a desired output format, using only a dataset for guidance.

## Overview

The core idea is to leverage the reasoning capabilities of an LLM to discover an effective prompt by analyzing input-output examples. We start with a basic instruction and iteratively refine it based on performance against a validation set.

1.  **Dataset:** A dataset containing short stories (input) and their corresponding structured YAML representations (output) is used.
2.  **Splitting:** The dataset is split into training, validation, and testing sets, similar to traditional ML workflows.
3.  **Prompt Discovery (`discover_prompt`):**
    *   The LLM is initially prompted to create a transformation prompt based on the training samples.
    *   This generated prompt is then used to process the validation set.
    *   Accuracy is calculated by comparing the LLM's output with the expected YAML output.
    *   The LLM receives feedback (previous prompt, accuracy, mismatches) and refines the prompt subsequent "epochs".
    *   This loop continues until a satisfactory accuracy is achieved on the validation set.
4.  **Testing (`test_prompt`):** The final, refined prompt is evaluated against the unseen testing set to gauge its generalization performance.

## Why is this important?

This example highlights how **datasets can drive development in Generative AI projects**. Instead of manually engineering complex prompts, we can guide the LLM to discover them by providing clear examples of the desired transformation. This approach uses the dataset for:

*   **Training:** Providing examples for the LLM to learn the transformation.
*   **Validation:** Guiding the prompt refinement process ("hyperparameter tuning").
*   **Testing:** Evaluating the final prompt's effectiveness on unseen data.

---

**See [generative-learning.ipynb](generative-learning.ipynb)** ( [📔](https://nbsanity.com/intellectronica/generative-learning/blob/main/generative-learning.ipynb) )

---

If you liked this demo and are looking for more, visit my [AI Expertise hub](https://ai.intellectronica.net/) and [subscribe to my newsletter](https://sub.ai.intellectronica.net/) (low volume, high value).