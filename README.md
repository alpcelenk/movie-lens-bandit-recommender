# MovieLens Bandit Recommendation System

This project compares two Multi-Armed Bandit algorithms using the MovieLens dataset:

- Thompson Sampling (TS)
- Upper Confidence Bound (UCB)

The goal is to learn the most rewarding movie genre based on user ratings and recommend highly rated movies from that genre.

---

# Dataset

The project uses the MovieLens dataset:

- `movies.csv`
- `ratings.csv`

## movies.csv

Contains:

- movieId
- title
- genres

Example:

| movieId | title | genres |
|---|---|---|
| 1 | Toy Story (1995) | Adventure\|Animation\|Children\|Comedy\|Fantasy |

---

## ratings.csv

Contains:

- userId
- movieId
- rating
- timestamp

Example:

| userId | movieId | rating |
|---|---|---|
| 1 | 16 | 4.0 |

---

# Project Structure

```text
movie-lens-bandit-recommender/
│
├── data/
│   ├── movies.csv
│   └── ratings.csv
│
├── notebooks/
│   ├── ts_movie_lens.ipynb
│   └── ucb_movie_lens.ipynb
│
└── README.md
```

---

# Reward Definition

The reward was converted into a binary format:

```python
reward = 1 if rating >= 4 else 0
```

Meaning:

- `1` → user liked the movie
- `0` → user did not like the movie

---

# Thompson Sampling

Thompson Sampling is a probabilistic Multi-Armed Bandit algorithm.

For each genre:

- Successes and failures are tracked
- A Beta distribution is created
- Random samples are drawn
- The genre with the highest sample is selected

## Characteristics

- Probabilistic exploration
- Handles uncertainty naturally
- More stochastic behavior
- Balances exploration and exploitation dynamically

---

# Upper Confidence Bound (UCB)

UCB selects actions using:

\[
Q(a) + \sqrt{\frac{3}{2}\frac{\ln(n)}{N(a)}}
\]

Where:

- `Q(a)` = average reward
- `n` = current timestep
- `N(a)` = number of selections

## Characteristics

- Confidence-bound based exploration
- More deterministic behavior
- Faster exploitation
- Quickly focuses on high-performing genres

---

# Results

Both algorithms selected:

```text
Drama
```

as the best genre.

This result is reasonable because:

- Drama appears frequently in the dataset
- Drama contains many highly rated movies
- The dataset contains popularity bias toward Drama movies

---

# Thompson Sampling vs UCB

| Feature | Thompson Sampling | UCB |
|---|---|---|
| Exploration Type | Probabilistic | Confidence-based |
| Behavior | More stochastic | More deterministic |
| Exploitation Speed | Medium | Fast |
| Uncertainty Handling | Natural | Formula-based |
| Best Genre | Drama | Drama |

---

# Top Recommended Movies

## Thompson Sampling

1. Paths of Glory (1957)
2. All Quiet on the Western Front (1930)
3. Kundun (1997)
4. Nausicaä of the Valley of the Wind (1984)
5. Cinema Paradiso (1989)

---

## UCB

1. Paths of Glory (1957)
2. All Quiet on the Western Front (1930)
3. Kundun (1997)
4. Nausicaä of the Valley of the Wind (1984)
5. Cinema Paradiso (1989)

---

# Visualizations

The project includes:

- Genre selection histograms
- Cumulative reward graphs
- Average reward comparisons
- Thompson Sampling Beta sample visualizations

---

# Key Takeaways

This project demonstrates:

- Exploration vs exploitation tradeoff
- Recommendation systems using bandit algorithms
- Online learning concepts
- Bayesian sampling with Thompson Sampling
- Confidence-bound exploration with UCB
- Popularity bias in recommendation systems

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib

---

# Future Improvements

Possible future extensions:

- User-specific recommendations
- Contextual bandits
- Deep Reinforcement Learning
- Personalized Thompson Sampling
- Regret analysis
- Hybrid recommendation systems

---

# Author

Alp Çelenk
