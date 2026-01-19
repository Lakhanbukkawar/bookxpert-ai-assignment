# Task 1: Get Matching Person Names

## Objective

Build a name-matching system that identifies the most similar person names from a predefined dataset when a user inputs a name.

The system returns:

* The best matching name with a similarity score
* A ranked list of other similar names with their scores

---

## Problem Context

In real-world applications such as customer onboarding, CRM systems, and identity verification, the same person’s name may appear in multiple forms due to spelling variations, phonetic differences, abbreviations, or partial entries. This task demonstrates how such inconsistencies can be handled effectively using fuzzy string matching techniques.

---

## Approach

### Dataset Preparation

* Created a dataset of 50 person names.
* Included spelling variations, phonetic variations, short forms, and full names.

### Similarity Matching

* Used RapidFuzz for fuzzy string similarity.
* Applied the WRatio scorer to handle partial matches, reordered words, and typographical errors.

### Key Logic

* Normalized user input for case-insensitive matching.
* Applied threshold-based filtering to remove weak matches.
* Ranked results based on similarity scores.
* Handled edge cases internally, such as empty input and no-match scenarios.

---

## Project Structure

task1_name_matching/
└── task1_name_matching.ipynb

---

## How to Run

### Install Dependencies

pip install rapidfuzz

### Execute Notebook

Open the notebook `task1_name_matching.ipynb` and run all cells sequentially.

---

## Sample Input

Geeta

## Sample Output

Best Match:
Geetha (Similarity Score: 96%)

Other Matches:
Gita (90%)
Gitu (87%)
Geeta (95%)

---

## Features

* Case-insensitive matching
* Handles spelling mistakes and phonetic variations
* Returns JSON-compatible structured output
* Configurable parameters for number of results and similarity threshold
* Safe handling of empty and unknown inputs

---

## Edge Case Handling

| Scenario           | Behavior                         |
| ------------------ | -------------------------------- |
| Empty input        | Returns a clear error message    |
| No similar names   | Returns an empty match list      |
| Partial name input | Returns closest possible matches |

---

## Notes

* The solution is lightweight and runs fully offline.
* Designed to be extensible and suitable for production use.
* Can be scaled to large datasets using vector search techniques.

---

## Author

Lakhan Bukkawar
