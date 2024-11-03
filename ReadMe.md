# Movie Recommendation System

There are several types of recommendation system techniques including 
1. Collaborative Filtering
    A recommendation technique that suggests items (like movies, books, or products) to users based on the preferences or interactions of other users. The core idea is that users who agreed on items in the past are likely to agree again in the future.

2. Content-Based Filtering
    A recommendation technique that suggests items to users based on the attributes or features of the items themselves and the user’s past interactions with them. It focuses on the content and characteristics of items, rather than relying on user interactions or preferences from other users (as in Collaborative Filtering).

3. Hybrid Recommendation 
    Combines multiple recommendation techniques, usually blending Content-Based Filtering and Collaborative Filtering to leverage the strengths of each approach and mitigate their limitations. Hybrid systems aim to improve recommendation quality, especially in complex cases where a single method might fall short.


This is a Contention-based recommending system, which recommends movies with similar genres to the one provided.

## How it works
I. The system uses TF-IDF, a weighting system that assigns a weight to each word in a document based on its `term frequency (tf)` and the `reciprocal document frequency` `(tf)` `(idf)`, to transform the text data into numerical representation. The result in a matrix where each row represents a movie and each column represents a unique genre term, weighted by how important the term is within the genre descriptions across the entire dataset.

II. The system then calculates `Cosine similarity`, which measures the cosine of the angle between two vectors; a _smaller angle means greater similarity_. If two movies have similar genre words, they will have a high cosine similarity score. The result is a `similarity matrix`.

III. The `recommend_movies()` function takes a movie title as input and finds movies similar to it based on genre similarity.
    a. It locates the index of the input movie in the DataFrame (df[df['title'] == title].index[0]) and retrieves the similarity scores of all other movies to this one using cosine_sim.

    b. The movies are sorted by similarity score in descending order, and the top 3 most similar movies (excluding the original) are selected.

    c. the function returns the titles of the top 3 similar movies, based on genre similarity.

### How to run it
In the root direcory, 
1. run `pip install -r requirements.txt` to install dependencies
2. run `python main.py` to start the system.
In the console, input a movie name