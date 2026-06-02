# 🎬 Movie Recommendation System Using Python and Pandas

A beginner-friendly Python project that builds a **content-based Movie Recommender System** using the Pandas library and correlation analysis on the MovieLens dataset. Enter any movie title and get the top 4 recommended movies instantly.

[![Python](https://img.shields.io/badge/Python-3.6%2B-blue)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![Stars](https://img.shields.io/github/stars/rudrajikadra/Movie-Recommendation-System-Using-Python-and-Pandas)](https://github.com/rudrajikadra/Movie-Recommendation-System-Using-Python-and-Pandas/stargazers)
[![Forks](https://img.shields.io/github/forks/rudrajikadra/Movie-Recommendation-System-Using-Python-and-Pandas)](https://github.com/rudrajikadra/Movie-Recommendation-System-Using-Python-and-Pandas/forks)

---

## 📖 Overview 

This project demonstrates how to build a simple movie recommendation engine using **correlation** between user ratings. Given a movie title, the system finds other movies that have been rated similarly by users and recommends the top matches.

It is built on top of the [MovieLens dataset](https://grouplens.org/datasets/movielens/) and extends the work from [krishnaik06/Movie-Recommender-in-python](https://github.com/krishnaik06/Movie-Recommender-in-python) with an interactive text input feature.

---

## 📁 Project Structure

```
Movie-Recommendation-System-Using-Python-and-Pandas/
│
├── Movie Recommender System.ipynb   # Main Jupyter Notebook
├── dataset.csv                      # User ratings dataset
├── movieIdTitles.csv                # Movie ID to title mapping
├── MovieRecommendations.csv         # Output recommendations
└── README.md
```

---

## ✨ Features

- 📊 Uses **Pandas correlation** to find movie similarities based on user ratings
- 🔍 Interactive **text input bar** — type any movie title to get recommendations
- 🎯 Returns the **top 4 most similar movies** as recommendations
- 📁 Built on a subset of the **MovieLens dataset**
- 🔰 Beginner-friendly and fully contained in a single Jupyter Notebook

---

## 🔧 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/rudrajikadra/Movie-Recommendation-System-Using-Python-and-Pandas
cd Movie-Recommendation-System-Using-Python-and-Pandas
```

### 2. Install Dependencies

```bash
pip install pandas numpy jupyter ipywidgets
```

### 3. Launch the Notebook

```bash
jupyter notebook "Movie Recommender System.ipynb"
```

---

## 🚀 Usage

1. Open the notebook in Jupyter
2. Run all cells from top to bottom
3. In the input bar at the bottom, type a movie title (e.g. `Toy Story`)
4. The system will output the top 4 recommended movies based on correlation

**Example Output:**

```
Input: Toy Story (1995)

Recommended Movies:
1. Toy Story 2 (1999)
2. Bug's Life, A (1998)
3. Aladdin (1992)
4. Lion King, The (1994)
```

---

## 🧠 How It Works

The recommendation engine follows these steps:

1. **Load** the user ratings and movie title datasets
2. **Merge** them into a single DataFrame
3. **Pivot** the data to create a user-movie ratings matrix
4. **Compute correlation** between the target movie and all other movies using `DataFrame.corrwith()`
5. **Filter** results by a minimum number of ratings to remove noise
6. **Return** the top correlated movies as recommendations

```python
import pandas as pd

# Create movie matrix
movie_matrix = merged_df.pivot_table(index='user_id', columns='title', values='rating')

# Get ratings for the selected movie
movie_user_ratings = movie_matrix['Toy Story (1995)']

# Compute correlation with all other movies
similar_to_movie = movie_matrix.corrwith(movie_user_ratings)

# Filter and sort
corr_movie = pd.DataFrame(similar_to_movie, columns=['Correlation'])
corr_movie.dropna(inplace=True)
corr_movie = corr_movie.join(ratings_mean_count['rating_counts'])
corr_movie[corr_movie['rating_counts'] > 100].sort_values('Correlation', ascending=False).head()
```

---

## 📦 Dependencies

| Package | Purpose |
|---|---|
| `pandas` | Data manipulation and correlation analysis |
| `numpy` | Numerical operations |
| `jupyter` | Interactive notebook environment |
| `ipywidgets` | Text input widget for movie search |

---

## 📊 Dataset

The project uses a subset of the [MovieLens Dataset](https://grouplens.org/datasets/movielens/), which contains:

- **User ratings** for thousands of movies (`dataset.csv`)
- **Movie ID to title mapping** (`movieIdTitles.csv`)

---

## 🤝 Contributing

Contributions are welcome! To get started:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push the branch: `git push origin feature/your-feature`
5. Open a pull request

---

## 💬 Feedback & Support

Enjoyed this project? Drop a ⭐ on GitHub and share it with fellow developers — your support keeps open-source going!

---

*"Data is the new oil, and recommendations are the engine that drives it."*
