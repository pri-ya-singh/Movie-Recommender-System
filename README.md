# 🎬 Movie Recommender System

## 🚀 Project Aim
This project aims to recommend similar movies based on the selected input movie title using content-based filtering techniques.

---

## 📋 How to Use

To get started with this project, follow these steps:

1. **Clone the Repository:**  
   Download the project repository to your local machine.

2. **Install Required Packages:**  
   Use the `requirements.txt` file to install all necessary packages. Key packages include:
   - `pandas`
   - `numpy`
   - `scikit-learn`
   - `flask`

3. **Run the Application:**  
   Execute the `app.py` file to launch the web application.

---

## 📌 Project Description

### 🎯 What Does This Project Do?
This project recommends movies that are similar to the one selected by the user.  
![Movie Recommender System](https://github.com/pri-ya-singh/Movie-Recommender-System/blob/main/movie_rec_final.png)

---

## 🛠️ How Does This Project Work?

### 1. **Data Collection:**  
The system uses two datasets – `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` – which contain detailed information about movies, including titles, genres, overviews, cast, crew, and keywords.

### 2. **Feature Extraction:**  
Important features like genres, keywords, top 3 cast members, and the director are extracted from the dataset. These features are combined with the movie's overview to form a single text field called `tags`. The text data is then converted into numerical vectors using the **Bag of Words** model via `CountVectorizer`.

### 3. **Similarity Calculation:**  
Cosine similarity is applied to these vectors to calculate how similar one movie is to another. Based on this similarity matrix, the system ranks and recommends the top 5 most similar movies for a given input movie.

### 4. **Web Integration:**  
The recommendation logic and processed data are saved using `pickle`. These `.pkl` files are integrated into a Flask-based web application where users can select a movie from a dropdown and get content-based movie recommendations.

---

## 🧪 Example Usage

Here's a sample code snippet showing how similarity is calculated:

```python
from sklearn.metrics.pairwise import cosine_similarity

# TF-IDF feature matrix of movie descriptions
similarity_matrix = cosine_similarity(tfidf_matrix)

# Get index of the selected movie
movie_index = movies[movies['title'] == 'Harry Potter and the Philosopher\'s Stone'].index[0]

# Fetch similar movies
similar_movies = sorted(list(enumerate(similarity_matrix[movie_index])), reverse=True, key=lambda x: x[1])[1:6]

# Display top 5 recommendations
for i in similar_movies:
    print(movies.iloc[i[0]].title)
