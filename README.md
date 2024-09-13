# Tesla Stock Price Prediction using Time Series Models and Twitter Sentiment Analysis

This project aims to predict Tesla's stock prices using various deep learning models and sentiment analysis of Twitter data related to Tesla. The project explores different neural network architectures for time series forecasting and incorporates sentiment scores derived from Twitter to enhance prediction accuracy.

## Table of Contents

- [Overview](#overview)
- [Datasets](#datasets)
- [Time Series Prediction Models](#time-series-prediction-models)
  - [Conv-RNN Model](#conv-rnn-model)
  - [Conv-LSTM Model](#conv-lstm-model)
  - [Conv-Bidirectional LSTM Model](#conv-bidirectional-lstm-model)
- [Sentiment Analysis Models](#sentiment-analysis-models)
  - [Data Preprocessing](#data-preprocessing)
  - [Models Implemented](#models-implemented)
- [Results](#results)
  - [Time Series Models Performance](#time-series-models-performance)
  - [Sentiment Analysis Models Performance](#sentiment-analysis-models-performance)
- [Conclusion](#conclusion)
- [Requirements](#requirements)
- [Usage](#usage)
- [License](#license)

## Overview

The project is divided into two main parts:

1. **Time Series Prediction**: Utilizing historical stock price data to predict future stock prices using different neural network architectures.
2. **Twitter Sentiment Analysis**: Analyzing Twitter data related to Tesla to gauge public sentiment and using it to predict stock prices.

## Datasets

- **Tesla Stock Price Data**: Historical stock prices of Tesla, including Open, High, Low, Close prices.
- **Twitter Data**: Tweets mentioning Tesla over a period of 10 days.

## Time Series Prediction Models

### Conv-RNN Model

- Combines 1D Convolutional layers with Simple RNN layers.
- Aims to capture both spatial and temporal dependencies in the data.
- **Architecture**:
  - Conv1D layer with 128 filters.
  - Three Simple RNN layers with 64, 128, and 32 units respectively.
  - Dense layers to output predictions for High, Low, Open, and Close prices.

### Conv-LSTM Model

- Integrates 1D Convolutional layers with LSTM layers.
- Designed to handle temporal sequences more effectively than Simple RNN.
- **Architecture**:
  - Conv1D layer with 128 filters.
  - Three LSTM layers with 64, 128, and 32 units respectively.
  - Dense layers for final output.

### Conv-Bidirectional LSTM Model

- Employs Bidirectional LSTM layers to capture patterns in both forward and backward directions.
- **Architecture**:
  - Conv1D layer with 128 filters.
  - Three Bidirectional LSTM layers with 50 units each.
  - Dense layers for output.

## Sentiment Analysis Models

### Data Preprocessing

- **Tweet Aggregation**: Tweets are aggregated daily to match the stock data's time intervals.
- **Sentiment Scoring**: Each tweet is analyzed using NLTK's VADER Sentiment Analyzer to compute compound, negative, neutral, and positive scores.
- **Data Alignment**: The sentiment scores are merged with the corresponding stock closing prices.

### Models Implemented

- **Random Forest Regressor**
- **CatBoost Classifier**
- **Deep Neural Network (DNN)**

## Results

### Time Series Models Performance

| Model                | MAE High | MAE Low | MAE Open | MAE Close |
|----------------------|----------|---------|----------|-----------|
| **Conv-RNN**         | 34.03    | 33.99   | 48.78    | 33.50     |
| **Conv-LSTM**        | **33.52**    | **33.98**   | **34.47**    | **34.25**     |
| **Conv-Bidirectional LSTM** | 37.44    | 38.15   | 37.81    | 42.45     |

- The Conv-LSTM model outperformed the other models, achieving the lowest MAE across most stock price predictions.

### Sentiment Analysis Models Performance

| Model       | MAE      |
|-------------|----------|
| **Random Forest Regressor** | 116.20   |
| **CatBoost Classifier**     | **111.20**   |
| **Deep Neural Network**     | 177.55   |

- The CatBoost Classifier achieved the lowest MAE among the sentiment analysis models.

## Conclusion

- **Best Performing Model**: The Conv-LSTM model provides the most accurate predictions for Tesla's stock prices based on historical data.
- **Sentiment Analysis Impact**: Incorporating Twitter sentiment analysis did not outperform the time series models, suggesting that sentiment alone may not be sufficient for accurate stock price prediction.
- **Future Work**:
  - Combine time series data with sentiment features for a more robust predictive model.
  - Experiment with advanced models like Transformers for sequential data.

## Requirements

- Python 3.x
- Libraries:
  - numpy
  - pandas
  - matplotlib
  - seaborn
  - scikit-learn
  - tensorflow
  - keras
  - nltk
  - catboost

## Usage

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/Forecasting-the-Stock-prices-of-Tesla.git
   ```

2. **Install Requirements**:

   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Notebooks**:

   - Open the Jupyter notebooks for time series prediction and sentiment analysis.
   - Execute the cells sequentially.

4. **Data Files**:

   - Place the `tsla_stock_price.csv` and `tweet_tesla_data.csv` files in the project directory.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
