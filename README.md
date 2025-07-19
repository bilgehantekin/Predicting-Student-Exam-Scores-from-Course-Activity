# BİL 471 – Final Grade Prediction

This repository contains notebooks used to predict final exam grades using student submissions (Labs, Quizzes, LCs, and Projects). It combines handcrafted features and LLM-based similarity scores.

---

## Workflow Overview

To reproduce `final_results.ipynb`, follow the steps below **in order**:

### 1. Generate Model Answers
Use an LLM (e.g., Mistral-7B) to generate ideal reference answers for:

- `model_answers_for_Labs.ipynb`
- `model_answers_for_Quizzes.ipynb`
- `model_answers_for_Projects.ipynb`

These notebooks create reference responses and save them as `.json` or `.csv`.

---

### 2. Prepare Student Submissions
Extract and clean real student answers from raw files:

- `students_answers_for_Labs.ipynb`
- `students_answers_for_Quizzes.ipynb`
- `students_answers_for_Projects.ipynb`

---

### 3. Compute Similarity Scores
Use an embedding model (e.g., `MiniLM`) to calculate cosine similarity between reference and student responses:

- `model_and_students_similarity_for_Labs.ipynb`
- `model_and_students_similarity_for_Quizzes.ipynb`
- `model_and_students_similarity_for_Projects.ipynb`

Each notebook saves per-question similarity scores by UID.

---

### 4. Extract Handcrafted Features
Compute statistical or structural features from submissions:

- `Lab_hand-crafted_features.ipynb`
- `Quiz_hand-crafted_features.ipynb`
- `Project_hand-crafted_features.ipynb`
- `LC_hand-crafted_features.ipynb`

---

### 5. Run Final Grade Prediction
Train regression models on the combined feature set and output test predictions:

- `final_results.ipynb`

This notebook:
- Merges all feature files by `UID`
- Trains multiple models (e.g., Random Forest, XGBoost)
- Saves validation results, predictions, and `.joblib` model files

---

## 🛠 Requirements

```bash
pip install -r requirements.txt
