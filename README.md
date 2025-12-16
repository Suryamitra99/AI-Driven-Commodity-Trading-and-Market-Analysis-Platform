# AI-Driven Commodity Trading and Market Analysis Platform

A comprehensive machine learning platform for analyzing commodity markets and generating automated trading signals using historical price data, sentiment analysis, and advanced predictive models.

##  Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Supported Commodities](#supported-commodities)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Workflow](#workflow)
- [Results](#results)
- [API Keys](#api-keys)
- [Contributing](#contributing)
- [License](#license)

##  Overview

This platform provides an end-to-end solution for commodity trading analysis, combining:

- **Data Collection**: Automated fetching of historical commodity futures data from Yahoo Finance
- **Data Processing**: Comprehensive cleaning, preprocessing, and feature engineering
- **Exploratory Analysis**: Statistical analysis, correlation matrices, and visualization
- **Sentiment Analysis**: Real-time news sentiment analysis using VADER sentiment analyzer
- **Technical Indicators**: Moving averages, RSI, MACD, Bollinger Bands, and more
- **Strategy Backtesting**: Multiple trading strategies with performance evaluation
- **Machine Learning**: XGBoost-based price prediction models with hyperparameter tuning
- **Signal Generation**: Automated trading signal generation based on model predictions
- **Performance Tracking**: PnL calculation and visualization

##  Features

### 1. Data Management
- Automated data fetching from Yahoo Finance for 10 major commodities
- Data cleaning and preprocessing pipeline
- Historical data from 2014 to present
- CSV-based data storage and management

### 2. Technical Analysis
- **Moving Averages**: 10-day, 30-day, and 50-day moving averages
- **Exponential Moving Average (EMA)**: 10-day EMA
- **Bollinger Bands**: Upper, middle, and lower bands with 2 standard deviations
- **Relative Strength Index (RSI)**: 14-day RSI for overbought/oversold conditions
- **MACD**: Moving Average Convergence Divergence with signal line
- **Daily Returns**: Percentage change calculations

### 3. Sentiment Analysis
- Real-time news article fetching from NewsAPI
- VADER sentiment analysis for each commodity
- Sentiment classification (Positive, Neutral, Negative)
- Sentiment score aggregation and trend analysis

### 4. Trading Strategies
- **Momentum Strategy**: Based on price momentum and EMA crossovers
- **Range Trading Strategy**: Using Bollinger Bands for support/resistance levels
- **Breakout Strategy**: Identifying price breakouts above/below moving averages
- **Mean Reversion Strategy**: Combining RSI and price deviation from moving average
- **Seasonal Strategy**: Month-based trading signals
- **News-Based Strategy**: Integrating sentiment analysis with technical indicators

### 5. Machine Learning
- XGBoost regression models for price prediction
- Hyperparameter tuning using GridSearchCV with TimeSeriesSplit
- Train/test/hidden data split (70%/20%/10%)
- Model evaluation with MAE and RMSE metrics

### 6. Signal Generation & Trading
- Automated trading signal generation (Buy/Sell/Hold)
- Signal-based trading execution
- Cumulative PnL calculation and visualization
- Performance metrics for each commodity

##  Supported Commodities

1. **Crude Oil** (CL=F)
2. **Coffee** (KC=F)
3. **Natural Gas** (NG=F)
4. **Gold** (GC=F)
5. **Wheat** (ZW=F)
6. **Cotton** (CT=F)
7. **Corn** (ZC=F)
8. **Sugar** (SB=F)
9. **Silver** (SI=F)
10. **Copper** (HG=F)

## Technologies Used

- **Python 3.11+**
- **Data Processing**: pandas, numpy
- **Data Fetching**: yfinance
- **Machine Learning**: scikit-learn, xgboost
- **Sentiment Analysis**: vaderSentiment
- **News API**: NewsAPI (via requests)
- **Visualization**: matplotlib, seaborn
- **Environment**: Jupyter Notebook

##  Installation

### Prerequisites

- Python 3.11 or higher
- pip package manager
- Jupyter Notebook or JupyterLab

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd AI-Driven-Commodity-Trading-and-Market-Analysis-Platform
```

### Step 2: Install Required Packages

```bash
pip install yfinance pandas numpy matplotlib seaborn scikit-learn xgboost vaderSentiment requests
```

Or install from a requirements file (if available):

```bash
pip install -r requirements.txt
```

### Step 3: Set Up API Keys

Create a `.env` file or configure your NewsAPI key (see [API Keys](#api-keys) section).

## Configuration

### NewsAPI Configuration

The platform requires a NewsAPI key for sentiment analysis. Update the API key in the notebook:

```python
api_key = 'YOUR_NEWSAPI_KEY_HERE'
```

You can obtain a free API key from [NewsAPI.org](https://newsapi.org/).

##  Usage

### Running the Complete Pipeline

1. **Open the Jupyter Notebook**:
   ```bash
   jupyter notebook Commodity_Trader_AI.ipynb
   ```

2. **Execute Cells Sequentially**:
   - The notebook is organized into sections that should be run in order
   - Each section builds upon the previous one

3. **Data Collection** (Cells 1-2):
   - Fetches historical data for all commodities
   - Saves data to `commodity_data/` directory

4. **Data Cleaning** (Cells 3-9):
   - Cleans and preprocesses the raw data
   - Creates cleaned CSV files with `_cleaned.csv` suffix

5. **Exploratory Data Analysis** (Cells 11-15):
   - Generates summary statistics
   - Creates visualizations and correlation matrices

6. **Sentiment Analysis** (Cells 16-20):
   - Fetches and analyzes news articles
   - Generates sentiment scores and classifications

7. **Feature Engineering** (Cells 22-38):
   - Adds technical indicators to the data
   - Creates feature-enhanced datasets

8. **Strategy Backtesting** (Cells 39-46):
   - Tests multiple trading strategies
   - Identifies best strategy for each commodity

9. **Machine Learning** (Cells 53-61):
   - Trains XGBoost models
   - Fine-tunes hyperparameters
   - Generates price predictions

10. **Signal Generation & Trading** (Cells 62-72):
    - Generates trading signals
    - Executes trades on hidden test data
    - Calculates and visualizes PnL

### Running Individual Sections

You can run specific sections independently if you have the required data files already generated.

##  Project Structure

```
AI-Driven-Commodity-Trading-and-Market-Analysis-Platform/
│
├── Commodity_Trader_AI.ipynb          # Main Jupyter notebook
├── README.md                           # This file
│
├── commodity_data/                     # Commodity price data
│   ├── crude_oil.csv
│   ├── crude_oil_cleaned.csv
│   ├── crude_oil_features.csv
│   └── ... (similar files for other commodities)
│
├── sentiment_data/                     # Sentiment analysis results
│   ├── cleaned_sentiment_data.csv
│   └── commodity_sentiment_summary.csv
│
├── xgboost_predictions_*.csv          # XGBoost prediction results
├── finetuned_xgboost_predictions_*.csv # Fine-tuned model predictions
├── signals_*.csv                      # Generated trading signals
├── commodity_strategy_cumulative_returns.csv
├── best_trading_strategy_per_commodity.csv
└── final_trading_results.csv          # Final PnL results
```

##  Workflow

```
1. Data Collection
   ↓
2. Data Cleaning & Preprocessing
   ↓
3. Exploratory Data Analysis
   ↓
4. Sentiment Analysis (Parallel)
   ↓
5. Feature Engineering
   ↓
6. Strategy Backtesting
   ↓
7. Machine Learning Model Training
   ↓
8. Hyperparameter Tuning
   ↓
9. Signal Generation
   ↓
10. Trading Execution & PnL Calculation
```

##  Results

### Model Performance

The fine-tuned XGBoost models achieve the following test set performance:

| Commodity | MAE | RMSE |
|-----------|-----|------|
| Crude Oil | 1.32 | 1.65 |
| Coffee | 13.01 | 18.20 |
| Natural Gas | 0.77 | 1.33 |
| Gold | 23.44 | 30.61 |
| Wheat | 98.99 | 163.18 |
| Cotton | 11.64 | 19.19 |
| Corn | 26.39 | 38.89 |
| Sugar | 1.14 | 1.85 |
| Silver | 0.45 | 0.57 |
| Copper | 0.09 | 0.11 |

### Trading Performance (Hidden Test Set)

Final PnL results on the hidden 10% test set:

| Commodity | Final PnL (%) |
|-----------|---------------|
| Natural Gas | 141.42% |
| Coffee | 137.53% |
| Crude Oil | 49.24% |
| Sugar | 48.15% |
| Wheat | 44.29% |
| Silver | 36.89% |
| Cotton | 22.27% |
| Corn | 14.00% |
| Gold | 5.91% |
| Copper | 2.63% |


##  API Keys

### NewsAPI

1. Sign up at [NewsAPI.org](https://newsapi.org/)
2. Get your free API key (500 requests/day on free tier)
3. Update the `api_key` variable in the sentiment analysis section of the notebook

```python
api_key = 'your-api-key-here'
```

**Important**: Never commit API keys to version control. Consider using environment variables or a `.env` file.

##  Future Enhancements

- [ ] Real-time data streaming integration
- [ ] Additional machine learning models (LSTM, Transformer-based models)
- [ ] Portfolio optimization and risk management
- [ ] Web dashboard for visualization
- [ ] Automated trading execution via broker APIs
- [ ] Multi-timeframe analysis
- [ ] Integration with additional data sources (weather, economic indicators)
- [ ] Advanced risk metrics (Sharpe ratio, maximum drawdown)
- [ ] Ensemble methods combining multiple models
- [ ] Real-time alert system



