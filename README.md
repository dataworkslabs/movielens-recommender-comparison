# MovieLens Recommender Comparison

This project builds and compares three recommender systems on the MovieLens
dataset using R and recommenderlab. It was done for a recommender systems
course assignment.

## What it does

It implements three recommenders and a baseline:

- User-user collaborative filtering (UBCF)
- Item-item collaborative filtering (IBCF)
- Content-based filtering from movie genres (TF-IDF weighted)
- POPULAR as a non-personalized baseline

It scores each method with RMSE and MAE. It also runs experiments that vary
neighborhood size, normalization, and the similarity metric.

## Data

Uses MovieLens ml-latest-small (about 100,000 ratings, 610 users, 9,724 movies).
Download it here: https://grouplens.org/datasets/movielens/

Unzip it and put `ratings.csv` and `movies.csv` in the same folder as the Rmd.
The data is not included in this repo.

## How to run

1. Install the packages:
```r
   install.packages(c("recommenderlab", "ggplot2"))
```
2. Put the Rmd and the two CSV files in the same folder.
3. Open `recommender_assignment.Rmd` in RStudio and knit it.

## Files

- `recommender_assignment.Rmd` - all code, experiments, and the writeup

## Main findings

- The two CF methods reacted to neighborhood size in opposite ways. Item-item
  CF had a low point near k = 30 and then got worse. User-user CF kept improving
  up to about k = 150. The two lines crossed near k = 50.
- Normalization mattered more than the similarity metric. Z-score plus Pearson
  was the best mix.
- No personalized method beat the POPULAR baseline (RMSE 0.881). This held under
  two different test protocols. This is a known result on MovieLens.
- Content-based filtering nearly matched the CF methods using only genres, and
  it can handle new movies that have no ratings yet.
