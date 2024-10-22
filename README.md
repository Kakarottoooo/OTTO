# Project Name: Otto Recommender System

This project involves training and validating models to predict user interactions with the Otto Recommender System dataset. The steps below detail data downloading, model training, validation, and generating predictions.

## Environment and Requirements

### Key Dependencies
Make sure the following Python packages are installed before running the code:

```bash
pip install pandas numpy lightgbm cudf gensim
```

### Hardware Requirements
- **Memory**: At least 128 GB of RAM is recommended.
- **Runtime**: The code may take up to 48 hours to run fully.
- **GPU**: It is highly recommended to use Kaggle's GPU environment for faster processing.

## Steps to Run

### Step 1: Download the Datasets

Download the required datasets into the `input` folder from the following links:

- [OTTO Chunk Data in Parquet Format](https://www.kaggle.com/datasets/columbia2131/otto-chunk-data-inparquet-format)
- [OTTO Validation Data](https://www.kaggle.com/datasets/cdeotte/otto-validation)
- [OTTO Recommender System Competition Data](https://www.kaggle.com/competitions/otto-recommender-system/data)
- [OTTO Full Optimized Memory Footprint](https://www.kaggle.com/datasets/radek1/otto-full-optimized-memory-footprint)

### Step 2: Train the Word2Vec Model

Train the Word2Vec model using the `word2vec-train.ipynb` notebook. It is recommended to use Kaggle's GPU for faster training.

### Step 3: Model Validation

Run the following validation steps sequentially:

1. **Recall Program**:
   ```bash
   code/recall_valid.ipynb
   ```
   - **Recommendation**: Use Kaggle’s GPU for this task.
   
2. **Feature Preparation**:
   ```bash
   code/feature_prepare_valid.ipynb
   ```

3. **Ranking Model**:
   ```bash
   code/rank_model_valid.ipynb
   ```
   - The model can be run for three types of interactions: `clicks`, `carts`, and `orders`.
   - You can modify the parameter `t` to specify the type (`t=clicks/carts/orders`).
   - The default recall quantity is 50, but you can increase it up to 250 for better results (more recall generally improves the score).

### Step 4: Model Prediction

Run the following steps sequentially for test data to generate the final submission file:

1. **Recall Program**:
   ```bash
   code/recall_test.ipynb
   ```
   - **Recommendation**: Use Kaggle’s GPU for this task.

2. **Feature Preparation**:
   ```bash
   code/feature_prepare_test.ipynb
   ```

3. **Ranking Model**:
   ```bash
   code/rank_model_test.ipynb
   ```
   - This will generate the final submission file: `submission.csv`.
