# 🎬 Movie Recommendation System using Content-Based Filtering

This project implements a content-based movie recommendation system using TF-IDF vectorization and cosine similarity. It suggests movies similar to the user's favorite movie based on textual features such as genres, cast, director, keywords, and tagline.

---

## Dataset

The dataset used is a CSV file (`movies.csv`) consisting of metadata about 4,803 movies. It includes various features but here are the top 5 relevant features picked for this project:

| Feature               | Description                                                        |
|------------------------|--------------------------------------------------------------------|
| genres                | Genres of the movie (as a stringified list of dictionaries)        |
| keywords              | Keywords describing the movie's plot/theme (stringified list)      |
| tagline               | Movie tagline                                                      |
| cast                  | Main actors in the movie                                           |
| director              | Director of the movie                                              |

These selected features are combined into a single textual feature and used to compute content similarity between movies.

---

## Libraries Used

- `pandas` – Data manipulation  
- `numpy` – Numerical operations  
- `scikit-learn` – TF-IDF vectorization and cosine similarity  
- `difflib` – Fuzzy string matching for movie title input  

---

## Workflow

### 1. Data Loading & Exploration
- Load the dataset using `pandas`
- Preview first/last rows, check shape and missing values

### 2. Preprocessing
- Select relevant content features: `genres`, `keywords`, `tagline`, `cast`, and `director`
- Fill missing values with empty strings
- Combine selected features into one string for each movie

### 3. Vectorization
- Convert the combined text into numerical form using `TfidfVectorizer`

### 4. Similarity Computation
- Compute the cosine similarity between all movie vectors

### 5. Recommendation Logic
- Input: User enters a favorite movie
- Use `difflib.get_close_matches` to find the best match from dataset
- Retrieve index and similarity scores
- Recommend top 9 most similar movies (excluding the input movie)

---

## Example Prediction

**User input:** `Enter your favourite movie name: the dictator`  
**System output:**  
Movies suggested for you:

1 . The Dictator  
2 . Borat: Cultural Learnings of America for Make Benefit Glorious Nation of Kazakhstan  
3 . Brüno  
4 . Les Misérables  
5 . Talladega Nights: The Ballad of Ricky Bobby  
6 . Madagascar  
7 . Million Dollar Arm  
8 . Madagascar 3: Europe's Most Wanted  
9 . Hugo

---

## How to Run

Follow these steps to set up and run the Movie Recommendation System locally:

1. **Clone the Repository**
```bash
git clone https://github.com/araa2105/Movie_Recommendation_System.git
cd Movie_Recommendation_System
```


2. **Install Dependencies**

    Make sure you have Python 3.8+ installed. Then install the required packages:

    ```bash
    pip install -r requirements.txt
    ```

3. **Add the Dataset**

    Place the `movies.csv` file in the root directory of the project.  
    If your dataset is elsewhere or has a different name, update this line in the script:

    ```python
    movie_data = pd.read_csv('movies.csv')
    ```

4. **Run the Notebook**

      ```bash
      jupyter notebook Movie_Recommendation_System_Content_and_Popularity_based.ipynb
      ```

## Improvements

- **Weighting Important Features**: Assign higher weight to fields like `genres` or `director` during vectorization to reflect their stronger influence on similarity.
- **Use Advanced Embeddings**: Replace TF-IDF with Word2Vec, Doc2Vec, or BERT embeddings for semantic similarity.
- **Web Interface**: Build a frontend using **Streamlit** or **Flask** to allow users to get recommendations through a simple UI.
