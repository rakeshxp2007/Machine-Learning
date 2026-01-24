# Revise Recommendation System (Google Colab Notebooks)

This repo is a **Colab-first mini project** that teaches and demonstrates the most common recommendation system approaches using small, runnable examples.

If you only read this README, you should know **exactly what each notebook does**, what you’ll see in output, and what concepts/algorithms are implemented.

## What you’ll learn

- **Content-based filtering** using **TF‑IDF** and **cosine similarity**
- **Collaborative filtering** using **user-user** and **item-item** similarity
- **Rating prediction** via **k-nearest neighbors (k=3)** style weighted averaging
- A practical **hybrid recommender** by combining content and collaborative scores with tunable weights

## Open in Google Colab (recommended)

Each notebook already includes a Colab badge inside it. You can also use these direct links:

- **Content-Based Filtering**: `https://colab.research.google.com/github/jyotidabass/Revise-Recommendation-system/blob/main/Content_Based_Filtering.ipynb`
- **User-Based Collaborative Filtering**: `https://colab.research.google.com/github/jyotidabass/Revise-Recommendation-system/blob/main/User_based_Collaborative_Filtering.ipynb`
- **User-based + Item-based Collaborative Filtering**: `https://colab.research.google.com/github/jyotidabass/Revise-Recommendation-system/blob/main/Collaborative_Filtering_User_based_and_Item_based.ipynb`
- **Hybrid Recommendation (Practical Implementation)**: `https://colab.research.google.com/github/jyotidabass/Revise-Recommendation-system/blob/main/Practical_Hybrid_Implementation.ipynb`

In Colab:

- **Runtime → Run all** (or run cells top-to-bottom)
- No external dataset download is required (everything is created inside the notebooks)

## Repository structure

All notebooks are inside:

- `Revise-Recommendation-system-main/`
  - `Content_Based_Filtering.ipynb`
  - `User_based_Collaborative_Filtering.ipynb`
  - `Collaborative_Filtering_User_based_and_Item_based.ipynb`
  - `Practical_Hybrid_Implementation.ipynb`

## What to expect in the code (by notebook)

### 1) `Content_Based_Filtering.ipynb` (TF‑IDF + cosine similarity)

- **Input**: a small movie “database” with `title` + `description` text
- **Core idea**: convert text → TF‑IDF vectors → cosine similarity between movies
- **Expected output**:
  - TF‑IDF matrix shape (e.g., `(6, 54)`)
  - A **similarity matrix** showing which movies are textually similar

### 2) `User_based_Collaborative_Filtering.ipynb` (user-user similarity + rating prediction)

- **Input**: a ratings matrix where rows = users, columns = movies, values = 1–5, `0` = not rated
- **Core idea**:
  - compute **cosine similarity between users**
  - for an unrated movie, use **top-k similar users** to predict a rating (weighted average)
- **Expected output**:
  - ratings table (users × movies)
  - **user similarity matrix**
  - predicted ratings / top recommendations for a target user

### 3) `Collaborative_Filtering_User_based_and_Item_based.ipynb` (walkthrough)

- **Input**: the same style ratings matrix as above
- **Core idea**:
  - demonstrates the flow/logic of collaborative filtering
  - includes concepts for both **user-based** and **item-based** similarity
- **Expected output**:
  - similarity matrices + prediction/recommendation steps (tutorial-style)

### 4) `Practical_Hybrid_Implementation.ipynb` (content + collaborative, weighted)

- **Input**:
  - a `movies` table (`movie_id`, `title`, `description`)
  - a `ratings` table (`user_id`, `movie_id`, `rating`)
- **Core idea**:
  - build **content similarity** from descriptions (TF‑IDF)
  - build **collaborative similarity** from the user-item matrix (item-item cosine similarity)
  - combine them:
    - `hybrid_score = content_weight * content_score + collab_weight * collab_score`
- **Expected output**:
  - content similarity matrix
  - user-item matrix
  - collaborative similarity matrix
  - hybrid recommendations printed with **content score**, **collab score**, and **final hybrid score**
  - comparison of different weight strategies (e.g., 80/20 vs 50/50 vs 20/80)

## Run locally (optional)

### Requirements

- Python 3.9+ recommended
- Libraries used: `pandas`, `numpy`, `scikit-learn`, `jupyter`

### Setup

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
# source .venv/bin/activate

pip install -U pip
pip install pandas numpy scikit-learn jupyter
```

### Launch

```bash
cd Revise-Recommendation-system-main
jupyter notebook
```

Open any `.ipynb` and run all cells.

## Notes / Troubleshooting

- **Import errors in VS Code**: select the correct Python interpreter (your `.venv`) in VS Code.
- **Colab**: if you get a “disconnected” runtime, just reconnect and re-run all cells.
