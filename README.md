# HMM-Based Alphabet Partitioning

Using Shakespeare’s Text for Unsupervised Character Classification

---

## 👤 Author Information

**Student Name:** Kaustubh Shivshankar Shejole

**Enrollment ID:** BT20CSE112

**Institution:** VNIT, Nagpur

---

## 📘 Overview

This project explores how a **Hidden Markov Model (HMM)** can learn structural patterns in English text and partition the alphabet into **two latent classes** without any supervision. By training on sequences from Shakespeare’s writings, the model organically separates characters into groups that align closely with **vowels** and **consonants**.

The work demonstrates how classical probabilistic models capture linguistic regularities and how hidden states can reveal meaningful language structure.

---

## 🎯 Objective

Train a 2-state HMM on sequential English text and use its **emission** and **transition** patterns to automatically divide the 26 lowercase letters (plus whitespace) into two classes.
The hypothesis: The model will learn something akin to **vowel vs. consonant** structure.

---

## 📂 Dataset

* **Source**: Complete works of William Shakespeare
* **Provider**: Project Gutenberg
* **URL**: `https://www.gutenberg.org/files/100/100-0.txt`

Only lowercase characters and whitespace were retained for modeling.

---

## 🛠️ Methodology

### 1. Preprocessing

* Scraped text via HTTP.
* Parsed with BeautifulSoup.
* Filtered to `[a–z]` and whitespace.
* Encoded characters as integer observations.

### 2. Model Setup

* **Hidden States**: 2
* **Observation Symbols**: 27 (letters + space)
* **Parameters**:

  * Initial distribution π
  * Transition matrix A
  * Emission matrix B

### 3. Training

* Algorithm: Baum–Welch (EM)
* Sequence length: 50,000 characters
* Epochs: 100
* Log-likelihood improved from ~–164,691 to ~–136,738

---

## 📈 Results

### Transition Matrix (Final)

```
[[0.3152, 0.6847],
 [0.7608, 0.2391]]
```

These high cross-state probabilities suggest alternating patterns, characteristic of **vowel–consonant** structures in English.

---

### Emission-Based Classification

#### **Class 1 — “Vowel-like + Whitespace”**

```
a, e, h, i, o, u, (space)
```

#### **Class 2 — “Consonant-like”**

```
b, c, d, f, g, j, k, l, m, n,
p, q, r, s, t, v, w, y
```

Notes:

* **x** and **z** were weakly assigned due to low emission differences.
* **h** joined the vowel-like class, likely due to its silent or transitional behavior in English.

---

## 📚 Interpretation

The HMM successfully discovered:

* A hidden alternation pattern between vowel-like and consonant-like states.
* Emission probabilities that match standard linguistic categories.
* Structure in text without supervision, highlighting the interpretability of classical models.

---

## 📝 Conclusion

This project shows that:

* HMMs can infer latent classes that align with linguistic categories.
* Even two hidden states can produce meaningful alphabet partitions.
* English text exhibits predictable phonotactic patterns that simple HMMs capture effectively.

---

## 📖 References

### Primary Reading

* Mark Stamp, *A Revealing Introduction to Hidden Markov Models*, SJSU (2018).

### YouTube Tutorials Used

* Introduction to HMMs (YouTube):
  [https://www.youtube.com/watch?v=PMIdkmXmZlg](https://www.youtube.com/watch?v=PMIdkmXmZlg)
* Baum–Welch / Forward–Backward explanation:
  [https://www.youtube.com/watch?v=fZ28ZmroMy8](https://www.youtube.com/watch?v=fZ28ZmroMy8)

---

