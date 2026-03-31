# Semantic Instability Detection using Embedding Drift

## 📌 Overview

This project investigates **semantic stability in language models** by analyzing how the meaning of a sentence changes when it is paraphrased or slightly modified.

Instead of training a model, this project focuses on **embedding analysis**, making it lightweight, fast, and research-relevant.

---

## 🎯 Objective

To detect whether **semantically similar sentences remain close in embedding space**, and identify cases where meaning representation becomes unstable.

---

## 🚀 Key Idea

For a given sentence:

1. Generate multiple semantically similar variants
2. Convert all sentences into embeddings
3. Compute similarity scores
4. Measure instability

---

## 🏗️ Architecture

```
Input Sentences
      ↓
Variant Generation
      ↓
Embedding Model (SBERT)
      ↓
Cosine Similarity
      ↓
Instability Score
      ↓
Analysis & Visualization
```

---

## 📂 Dataset

This project does **not require a training dataset**.

However, it uses:

* Autism-related text samples (provided dataset)
* Custom sentences (emotional, factual, ambiguous)

Example:

```
"I find social interaction difficult"
"I prefer routines"
"The sky is blue"
```

---

## ⚙️ Tech Stack

* Python
* Sentence-Transformers (SBERT)
* NumPy, Pandas
* Scikit-learn
* Matplotlib, Seaborn

---

## 🔧 Installation

```bash
pip install sentence-transformers
pip install numpy pandas scikit-learn matplotlib seaborn
```

---

## ▶️ Usage

### Step 1: Load Model

```python
from sentence_transformers import SentenceTransformer
model = SentenceTransformer('all-MiniLM-L6-v2')
```

### Step 2: Input Sentences

```python
sentences = [
    "I find social interaction difficult"
]
```

### Step 3: Generate Variants

```python
variants = [
    "I struggle with social interaction",
    "Social interactions are hard for me"
]
```

### Step 4: Compute Embeddings

```python
embeddings = model.encode([sentences[0]] + variants)
```

### Step 5: Compute Similarity

```python
from sklearn.metrics.pairwise import cosine_similarity
similarities = cosine_similarity([embeddings[0]], embeddings[1:])
```

### Step 6: Instability Score

```python
instability = 1 - similarities.mean()
```

---

## 📊 Sample Output

### Input

```
Original: "I find social interaction difficult"
Variants:
- "I struggle with social interaction"
- "Social interactions are hard for me"
```

### Similarity Scores

```
[0.91, 0.87]
```

### Instability Score

```
Instability = 1 - 0.89 = 0.11
```

👉 Interpretation: **Low instability → Meaning is preserved**

---

## 📈 Visualization Examples

### 1. Similarity Heatmap

| Sentence | Variant 1 | Variant 2 |
| -------- | --------- | --------- |
| Original | 0.91      | 0.87      |

### 2. Instability Comparison

| Category       | Avg Instability |
| -------------- | --------------- |
| Factual        | 0.08            |
| Emotional      | 0.18            |
| Autism-related | 0.21            |

---

## 🧠 Key Observations

* Factual sentences show **high stability**
* Emotional sentences show **moderate instability**
* Autism-related expressions show **higher variability**

---

## 🔍 Insights

* Language models are **not perfectly consistent** in representing meaning
* Subtle wording changes can lead to **embedding drift**
* This has implications for:

  * AI reliability
  * Mental health NLP systems
  * Bias and robustness studies

---

## 🚀 Future Work

* Compare multiple embedding models
* Add noise (typos, grammar errors)
* Use LLM-generated paraphrases
* Extend to multilingual analysis

---

## 🏁 Conclusion

This project demonstrates a simple yet powerful way to analyze **semantic consistency in NLP systems** using embedding similarity.

It highlights how even small changes in text can impact meaning representation.

---
