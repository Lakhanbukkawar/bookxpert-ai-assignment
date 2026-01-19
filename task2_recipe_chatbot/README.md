Task 2: Local LLM Integration & Recipe Chatbot

Objective
Build a locally runnable AI chatbot that suggests recipes based on user-provided ingredients using an open-source language model.

The system:

* Accepts ingredient input from the user
* Suggests a relevant recipe
* Exposes the functionality via a REST API
* Provides a chatbot-style interaction interface

---

Problem Context
Recipe recommendation is a common real-world application of AI assistants. Users often provide a limited set of ingredients and expect meaningful suggestions without relying on internet access or heavy infrastructure.

This task demonstrates how a lightweight local language model can be combined with a custom dataset and exposed through an API to deliver controlled and reliable responses on low-resource systems.

---

Approach

Model Selection
An open-source language model (google/flan-t5-small) is used.
It is chosen for its lightweight nature, CPU compatibility, and suitability for local execution.

Fine-Tuning Strategy
Instead of heavy model fine-tuning, a dataset-grounded generation approach is used:

* A custom recipe dataset is checked first
* The language model is used only as a fallback when no dataset match is found
* Prompt constraints are applied to reduce hallucinations

Core Logic

* Normalizes ingredient input (order- and plural-safe)
* Matches ingredients against a custom dataset using overlap logic
* Applies a confidence threshold for dataset-based selection
* Uses controlled language model generation only when required

---

Project Structure

task2_recipe_chatbot/
│
├── Local_LLM_Recipe_Chatbot.ipynb
├── recipes.json
└── requirements.txt

---

How to Run

Step 1: Install Dependencies
pip install -r requirements.txt

Step 2: Run the Notebook

* Open Local_LLM_Recipe_Chatbot.ipynb
* Run all cells sequentially
* The FastAPI server starts automatically in the background

---

API Usage

Endpoint
POST /get-recipe

Sample Request
{
"ingredients": "egg, onion"
}

Sample Response
{
"ingredients": "egg, onion",
"recipe": "Egg Onion Omelette: Beat eggs, sauté onions, cook until fluffy.",
"source": "dataset"
}

---

Chatbot Example

User: onion egg
Bot: Egg Onion Omelette

User: garlic cheese
Bot: A proper recipe cannot be made using only the given ingredients.

---

Features

* Fully local execution with no external API calls
* Handles ingredient order and plural variations
* Dataset-first matching for deterministic output
* Controlled language model fallback with guardrails
* JSON-based API responses

---

Edge Case Handling

Unknown ingredients
Returns a polite fallback message

Partial ingredient match
Uses dataset overlap logic

Extra ingredients
Avoids incorrect dataset matches

Empty input
Returns a clear validation message

---

Notes

* Designed for low-resource systems
* No GPU required
* Suitable for Google Colab and local environments

---

Author
Lakhan Bukkawar
