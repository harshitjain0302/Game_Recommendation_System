# Game Recommendation System (Steam)

Hybrid recommendation system combining **content-based filtering (TF-IDF + cosine similarity)** and **collaborative filtering (SVD)** to generate top-K personalized game recommendations on the Steam platform.

The project focuses on improving **game discovery and user engagement** by leveraging both item similarity and user–item interaction patterns, while addressing common recommender challenges such as **cold start** and **sparse user behavior**.

---

## Highlights
- Hybrid recommender: **content-based + collaborative filtering**
- Cold-start handling via content similarity
- Evaluated using **RMSE** and **ranking-based metrics**
- Emphasis on **product relevance and recommendation quality**, not just model accuracy

---

## Dataset
- **Source:** Steam games and user interaction data  
- **Entities:** users, games, ratings / interactions  
- **Key fields:**
  - `user_id`
  - `app_id`
  - `title`
  - `genres / tags`
  - `description`
  - `price`
  - `rating / interaction signal`

### Preprocessing
- Removed records with missing critical fields (ratings, titles)
- Cleaned and normalized textual fields
- Scaled numerical attributes (e.g., price, engagement ratios)
- Prepared user–item interaction matrix for collaborative filtering

---

## Approach

### 1. Content-Based Filtering
- Applied **TF-IDF vectorization** on game titles, descriptions, and tags
- Computed **cosine similarity** between games
- Recommended games with the highest similarity scores to a given item

This approach enables recommendations even when user interaction data is sparse or unavailable.

---

### 2. Collaborative Filtering
- Built a **user–item interaction matrix**
- Applied **Singular Value Decomposition (SVD)** using the Surprise library
- Learned latent factors representing user preferences and game characteristics
- Predicted unseen user–item ratings to generate personalized recommendations

---

### 3. Hybrid Strategy
- Combined collaborative predictions with content-based similarity
- Used content-based recommendations as a fallback for **cold-start users or games**
- Balanced personalization accuracy with recommendation coverage

---

## Evaluation

### Metrics Used
- **RMSE (Root Mean Squared Error):**  
  Evaluates rating prediction accuracy for collaborative filtering models.
- **Ranking-based evaluation (Top-K):**
  - Precision@K
  - Recall@K  
  These metrics better reflect real-world recommendation quality by focusing on the relevance of the top recommended items.

### Model Comparison
| Model | RMSE | Notes |
|------|------|------|
| Content-Based | — | Item similarity only |
| SVD (Collaborative) | ✓ | Strong personalization |
| Hybrid | ✓ | Best balance of relevance and coverage |

---

## Project Structure
Game_Recommendation_System/
├── notebooks/
│   ├── Preprocess.ipynb
│   └── Main.ipynb
├── Dataset.txt
├── README.md

---

## Key Insights
- Hybrid approaches outperform standalone models by balancing accuracy and coverage
- Collaborative filtering performs well for active users but struggles with cold-start scenarios
- Content-based similarity provides robust fallback recommendations when interaction data is sparse

---

## Limitations
- Offline evaluation only; no online A/B testing
- Relies on explicit or proxy interaction signals
- Label sparsity affects collaborative filtering performance

---

## Next Steps
- Add **implicit feedback signals** (e.g., playtime, clicks)
- Introduce **ANN-based similarity search (FAISS)** for scalability
- Deploy a lightweight **API or Streamlit demo** for interactive recommendations
- Extend evaluation with diversity and novelty metrics

---

## Tech Stack
- **Python**
- **Pandas, NumPy**
- **Scikit-learn**
- **Surprise (SVD)**
- **TF-IDF**
- **Matplotlib / Seaborn**
