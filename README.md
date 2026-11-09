# Spotify Music Recommendation System

A personalized music recommender built with **K-Nearest Neighbors (KNN)** on Spotify audio features. Given a user's favourite songs, the system finds the most similar tracks in feature space.

> **Status:** work in progress. This README is updated as each phase is completed.

## Dataset

[TidyTuesday 2020-01-21: Spotify Songs](https://github.com/rfordatascience/tidytuesday/tree/main/data/2020/2020-01-21)

- 32,833 rows and 23 columns in the raw file (tracks collected from six playlist genres via the Spotify API).
- Loaded directly from the raw GitHub URL inside the notebook, no manual download needed.
- Audio features used for similarity: `danceability`, `energy`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`, `duration_ms`.

## Project Structure

```
.
├── .github/workflows/   # CI/CD workflows (planned)
├── dataset/
│   ├── raw/             # raw data (not tracked by git)
│   └── processed/       # cleaned data (not tracked by git)
├── docs/                # diagrams and documentation (planned)
├── notebooks/
│   └── 01_data_exploration.ipynb
├── src/                 # source code
├── tests/               # tests (planned)
├── requirements.txt
└── README.md
```

## Setup

```bash
# create and activate a virtual environment
python -m venv .venv
.venv\Scripts\activate        # Windows
# source .venv/bin/activate   # macOS / Linux

# install dependencies
pip install -r requirements.txt
```

Then open `notebooks/01_data_exploration.ipynb` and select the `.venv` kernel.

## Roadmap

- [x] **Phase 1: Dataset research and EDA** (`notebooks/01_data_exploration.ipynb`)
- [ ] Phase 2: Data cleaning and preprocessing (scaling)
- [ ] Phase 3: KNN concepts and distance calculations
- [ ] Phase 4: KNN from scratch
- [ ] Phase 5: Personalized recommendations from favourite songs
- [ ] Phase 6: Evaluating recommendation quality
- [ ] Phase 7: Comparison with scikit-learn `NearestNeighbors`
- [ ] Phase 8: `validation_model.py` and model quality gate
- [ ] Phase 9: CI/CD with GitHub Actions
- [ ] Phase 10: Testing and final documentation

## Progress So Far

### Phase 1: Data exploration

- Removed 5 rows with missing track name, artist or album name (32,833 to 32,828).
- Removed duplicate `track_id` values, since the same song appears in multiple playlists, so each song is kept once (32,828 to 28,352).
- Converted audio features to `float64`, converted genre columns to `category` and stripped extra spaces from text columns.
- Features are on very different scales (`duration_ms`, `tempo` and `loudness` versus the 0 to 1 features), so **feature scaling is required** before KNN.
- `speechiness`, `acousticness`, `instrumentalness`, `liveness` and `loudness` are clearly skewed.
- Found 1 row with `tempo == 0` and 2 tracks shorter than 30 seconds. These will be handled in Phase 2.

## Methodology and Results

To be completed.

## Limitations

To be completed after evaluation.
