# Game Recommendation System (Steam)

Hybrid recommendation system combining content-based similarity and collaborative filtering (SVD) to generate personalized top-K game recommendations on the Steam platform.

This project focuses on improving game discovery by leveraging both user–item interaction patterns and game metadata, balancing personalization accuracy with coverage and cold-start robustness.

⸻

Highlights
	•	Implemented a hybrid recommender combining TF-IDF content similarity with matrix factorization (SVD)
	•	Addressed cold-start scenarios using content-based recommendations
	•	Evaluated models using rating accuracy (RMSE) and top-K ranking metrics
	•	Designed with a product-oriented framing focused on user engagement and relevance

⸻

Dataset
	•	Source: Steam games and user interaction dataset
	•	Entities: users, games, ratings / interactions
	•	Key fields:
	•	user_id, app_id
	•	rating (or implicit interaction signal)
	•	title, genre, description
	•	price, positive_ratio

Preprocessing
	•	Removed records with missing critical fields (ratings, titles)
	•	Cleaned and standardized textual features
	•	Normalized numerical features (e.g., price, engagement ratios)
	•	Prepared interaction matrices for collaborative filtering

⸻

Approach

1. Content-Based Filtering
	•	Vectorized game metadata (title, description, genre/tags) using TF-IDF
	•	Computed cosine similarity between games
	•	Recommended top-K games with highest similarity scores

Strengths:
	•	Works well for new or low-interaction items
	•	Interpretable recommendations

⸻

2. Collaborative Filtering
	•	Applied Singular Value Decomposition (SVD) using the Surprise library
	•	Learned latent user and item representations from historical interactions
	•	Predicted unseen user–item ratings to generate recommendations

Strengths:
	•	Captures collaborative signals and user preferences
	•	Scales well with interaction data

⸻

3. Hybrid Strategy
	•	Combined content-based similarity and SVD predictions to generate final recommendations
	•	Used content-based filtering as a fallback for cold-start users/items
	•	Enabled a balanced tradeoff between personalization accuracy and recommendation coverage

⸻

Evaluation

Metrics
	•	RMSE: Evaluates rating prediction accuracy for collaborative filtering
	•	Top-K Ranking Metrics:
	•	Precision@K
	•	Recall@K

Ranking metrics were used to assess how well the system surfaces relevant items in the top recommendations, which is more aligned with real-world recommender system objectives than rating accuracy alone.

(Exact values may vary based on train/test splits and interaction sparsity.)

⸻

Project Structure

Game_Recommendation_System/
├── notebooks/
│   ├── Preprocess.ipynb
│   └── Main.ipynb
├── Dataset.txt
├── README.md
└── requirements.txt

Key Insights
	•	Hybrid recommendations outperform single-method approaches in sparse and cold-start scenarios
	•	Content-based similarity provides strong initial relevance but benefits from collaborative signals for personalization
	•	Ranking metrics offer more actionable evaluation than RMSE alone for recommendation quality

⸻

Limitations
	•	Offline evaluation only (no online A/B testing)
	•	Sparse interaction data can reduce collaborative filtering performance
	•	No real-time personalization or feedback loop

⸻

Next Steps
	•	Add implicit feedback signals (e.g., playtime, clicks) to improve personalization
	•	Introduce diversity and novelty constraints in ranking
	•	Deploy a lightweight API or interactive demo (FastAPI / Streamlit)
	•	Optimize similarity search using approximate nearest neighbors (e.g., FAISS)
