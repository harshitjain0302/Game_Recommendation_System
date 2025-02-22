# Game Recommendation System on Steam

📌 Description

The Game Recommendation System is a machine learning project designed to help users on the Steam platform discover relevant games based on their preferences. By analyzing various attributes such as game features and user interactions, the system provides personalized game recommendations. This system uses both content-based filtering and collaborative filtering approaches to ensure users receive diverse and accurate suggestions.

The system helps users explore games they may like by utilizing a mix of collaborative filtering (based on user-item interactions) and content-based filtering (based on game features like title, genre, and description). The solution aims to enhance user engagement by streamlining the game discovery process, making it easier to find games that fit personal tastes.

🚀 Features

	•	Personalized Recommendations: Suggests games based on user preferences.
 
	•	Content-Based Filtering: Recommends games with similar features (e.g., title, genre).
 
	•	Collaborative Filtering: Provides recommendations based on user behavior and interactions.
 
	•	Evaluation Metrics: Uses RMSE to evaluate the recommendation system’s accuracy.
 
	•	Data Preprocessing: Handles missing values, encodes categorical data, and scales numerical features. 

🛠️ Tech Stack

	•	Python: Programming language for the development.
 
	•	Pandas: Data manipulation and analysis.
 
	•	NumPy: Numerical computing.
 
	•	Surprise: Library for collaborative filtering using SVD (Singular Value Decomposition).
 
	•	TF-IDF: Text feature extraction method for content-based filtering.
 
	•	Scikit-learn: Machine learning library for data preprocessing and metrics.
 
	•	Matplotlib/Seaborn: Data visualization.


📝 Data Preprocessing

Data preprocessing is a crucial step in transforming raw data into a usable format for the recommendation system. The following steps were performed:

	1.	Handling Missing Values: Rows with missing critical information (e.g., missing ratings or titles) were dropped.
 
	2.	Categorical Encoding: Features like platform and genre were label-encoded to convert them into numerical values suitable for machine learning.
 
	3.	Feature Scaling: Min-Max Scaling was applied to numerical columns like price and positive_ratio to normalize the data and bring all features to the same scale.
 
	4.	Text Processing: Game titles were processed using TF-IDF vectorization to standardize the text and remove unnecessary characters. This helps in capturing important features from the game titles and descriptions.

⚙️ Recommendation Techniques

Content-Based Filtering

	1.	TF-IDF Vectorization: The system uses TF-IDF (Term Frequency-Inverse Document Frequency) to vectorize the game titles and descriptions. This allows the system to calculate the similarity between games based on their textual features.
 
	2.	Cosine Similarity: Cosine similarity is used to calculate the similarity scores between games. Games with a high similarity score are recommended to the user.

Collaborative Filtering
	1.	Matrix Factorization: The system uses Singular Value Decomposition (SVD) from the Surprise library to decompose the user-item interaction matrix. This approach captures latent factors between users and items, which helps in generating personalized recommendations.
 
	2.	RMSE (Root Mean Squared Error): The RMSE metric is used to evaluate the accuracy of the collaborative filtering model by measuring the difference between the predicted and actual ratings.

