# Vibe-Check

## Project Overview
Vibe-Check is a neighborhood recommendation project based on the NYC 311 Service Requests dataset. Instead of focusing only on apartment price, size, or commute time, our project helps users evaluate whether a neighborhood matches their personal tolerance for urban issues such as noise, pests, sanitation problems, and infrastructure complaints.

Our goal is to build a user-facing system that helps renters identify New York City neighborhoods that better fit their quality-of-life preferences.

## Dataset
We use the NYC Open Data **311 Service Requests from 2020 to Present** dataset:

https://nycopendata.socrata.com/Social-Services/311-Service-Requests-from-2020-to-Present/erm2-nwe9/about_data

This dataset contains public complaint records with information such as complaint type, date, and location. It helps us analyze recurring neighborhood-level quality-of-life issues.

## User-Facing Question
Given a resident’s specific sensitivity to urban stressors—such as noise, pests, sanitation issues, or infrastructure failures—which NYC neighborhoods provide the best match for their preferences?

This question is interesting because apartment search platforms usually focus on price and amenities, while renters also care about everyday neighborhood conditions. A neighborhood may seem attractive on paper but still be a poor fit if it has many complaints related to issues the user especially wants to avoid.

## Method
Our method combines semantic matching, clustering, and recency-based scoring.

First, we use a pre-trained sentence-transformer embedding model and cosine similarity to match free-form user concerns to the most relevant complaint categories in the 311 dataset. This is appropriate because users may describe their concerns in natural language instead of using the exact complaint labels in the dataset.

Second, we use clustering methods such as k-means on the geographic coordinates of matched complaints to identify concentrated issue areas and generate neighborhood-level recommendations. This makes the output spatially interpretable and useful for decision-making.

Third, we apply recency weighting so that newer complaints have greater influence than older ones. This is important because neighborhood conditions change over time, and users care more about current liveability than historical patterns.

## Project Architecture

```text
Vibe-Check/
├── data/               # stores project data files
├── src/                # contains source code for preprocessing and recommendation logic
├── .gitignore          # specifies files ignored by Git
├── LICENSE             # project license
├── README.md           # project overview and design document
├── requirements.txt    # Python dependencies for the working environment
└── test_output.txt     # sample output or temporary testing results
