# Netflix-Movie-Recommender
## Table of Contents

1. [Overview](#overview)
2. [Project Structure](#project-structure)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Methodology](#methodology)
6. [Evaluation Metrics](#evaluation-metrics)
7. [Results](#results)
8. [Contributing](#contributing)


## Overview

This project aims to build a collaborative filtering-based movie recommendation system using the Netflix dataset. The system predicts the ratings that a specific user might give to different movies, helping to personalize content and improve user experience. The primary technique used in this project is **Singular Value Decomposition (SVD)**, a popular method for matrix factorization in recommendation systems.

## Project Structure

```
netflix_movie_recommendation/
├── dataset/
│   ├── netflix_dataset.zip
│   ├── netflix_movie_titles.csv
├── netflix_movie_recommendation_project.ipynb
├── README.md
├── requirements.txt
```

- **dataset/**: Contains the dataset files.
- **notebook Python file**: Jupyter notebooks for exploratory data analysis and model training.
- **README.md**: This README file.
- **requirements.txt**: Python dependencies required for the project.


## Installation

1. **Clone the repository**:

    ```bash
    git clone https://github.com/AnishMathewOommen/Netflix-Movie-Recommender.git
    cd Netflix-Movie-Recommender
    ```

2. **Install dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. **Data Preparation**:
   - Ensure the both dataset files are present in the `dataset/` directory.
   - Preprocess the data as needed (e.g., filtering, splitting).

2. **Model Training**:
   - Run the Jupyter notebook `netflix_movie_recommendation_project.ipynb` to train the SVD model and evaluate its performance.

3. **Generate Recommendations**:
   - Use the `netflix_movie_recommendation_project.ipynb` to generate movie recommendations for a specific user.
   - Example to predict ratings for user `2632461`:


## Methodology

### Data

- **Dataset**: The Netflix dataset `netflix_dataset.zip` used contains user IDs, movie IDs, and corresponding ratings. A subset of the data (100,000 rows) is used to make the computations manageable and efficient.
There is another dataset called the `netflix_movie_titles.csv` which contaings Movie IDs,Year and Movie name.
  
- **Columns**:
  - `Cust_Id`: Customer ID (unique identifier for users)
  - `Movie_Id`: Movie ID (unique identifier for movies)
  - `Rating`: User rating for the movie, on a scale from 1 to 5.
  - `Year`: Release Year of the Movie.
  - `Movie_name`: Name of the movie

### Model

- **Singular Value Decomposition (SVD)**: This is a matrix factorization technique that decomposes the user-item interaction matrix into the product of three matrices, capturing the latent features of both users and items.

- **Implementation**: The `surprise` library is used to implement SVD. This library provides tools to evaluate and train collaborative filtering models efficiently.

### Steps

1. **Data Loading**: The Netflix dataset is loaded into a Pandas DataFrame.
2. **Model Initialization**: An SVD model is initialized using the `surprise` library.
3. **Model Training**: The model is trained using a subset of the dataset (100,000 rows).
4. **Prediction**: The model predicts ratings for movies not yet rated by the user, based on learned user and movie latent features.
5. **Cross-Validation**: The model is evaluated using 3-fold cross-validation to assess its accuracy using the RMSE metric.

## Evaluation Metrics

- **Root Mean Squared Error (RMSE)**: The primary evaluation metric used to measure the difference between predicted and actual ratings. RMSE gives more weight to larger errors, making it suitable for this type of prediction task.

## Results

After running the cross-validation:

- **RMSE Mean**: Approximately 1.0185
- **RMSE Std**: 0.0013

These results indicate the model's predictive power is consistent and reasonably accurate, with predictions typically within 1 rating point of the actual rating.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.

