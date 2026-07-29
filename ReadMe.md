#  AI-Based Answer Evaluator

**Project Purpose:**
This automation evaluates a student's written answer against a model (ideal) answer using an LLM (Groq's Llama 3.3 70B). It returns a **Score out of 10** and **3–4 short bullet-point Remarks**, based on factual accuracy, completeness, and genuine conceptual understanding — not just keyword matching.

**How it works:**
1. The user provides a Question, a Model Answer, and a Student's Answer.
2. A carefully designed prompt instructs the LLM to act as a strict but fair examiner.
3. The LLM's response is parsed into a clean numeric score and a list of remarks.
4. Results are displayed in a color-coded, easy-to-read interface.

**Sections in this notebook:**
- Setup & API connection
- Core evaluation logic (prompt building, API call, parsing)
- A documented sample (Question / Model Answer / Student Answer) used as a demonstration
- An interactive visual interface to test any question live
## Core Evaluation Logic

This section contains four functions:
- `build_prompt()` — constructs the instructions sent to the LLM
- `get_evaluation()` — sends the prompt to Groq's API and returns the raw text response (wrapped in error handling in case the API call fails, e.g. due to network issues or rate limits)
- `parse_response()` — extracts a clean numeric score and a list of remarks from the LLM's raw text (safely handles unexpected formats instead of crashing)
- `evaluate_answer()` — the single reusable function that ties everything together

##  Sample Question, Model Answer & Student Answer

As required by the task, here is one documented sample used to demonstrate the automation:

**Question:** Explain why the heart is considered a double pump, and describe the path blood takes through its four chambers.

**Model Answer:** Describes the right side (pulmonary circulation) and left side (systemic circulation) of the heart, the full blood path through all four chambers and valves (tricuspid, mitral), and explains that this separation prevents oxygenated and deoxygenated blood from mixing.

**Student Answer:** A simplified version that correctly describes the general blood flow path (right atrium → right ventricle → lungs → left atrium → left ventricle → body) but omits valve names and the oxygen-mixing explanation.

Running the cell below evaluates this sample directly, as a working demonstration of the automation.

##  Interactive Interface

Pre-filled with the sample above — feel free to edit any field and click **Evaluate Answer** to test with your own question.