# Quantitative Value Investment Strategy

This Python project implements a quantitative value investing strategy that identifies and selects the 50 stocks with the strongest value metrics from the S&P 500. The strategy builds an equal-weight portfolio based on price-to-earnings (P/E) ratios.

### Features

* Fetches real-time stock data using the IEX Cloud API 
* Calculates and ranks stocks based on P/E ratios
* Filters out "glamour stocks" to focus on value opportunities
* Generates trade recommendations for an equal-weight portfolio
* Handles batch API processing for efficient data retrieval

### Dependencies

* numpy: For numerical computations
* pandas: For data manipulation and analysis  
* requests: For making HTTP requests to the IEX Cloud API
* xlsxwriter: For Excel file output
* scipy: For statistical calculations

### Installation
```pip install numpy pandas requests xlsxwriter scipy```

## Setup

- Create a secrets.py file containing your IEX Cloud API token: ```IEX_CLOUD_API_TOKEN = 'your_api_token_here'```
- Place your S&P 500 stocks list in sp_500_stocks.csv.
- Run the Jupyter notebook to:
- Import required libraries
- Load stock data
- Execute batch API calls
- Filter and rank stocks
- Generate portfolio recommendations
- Data Structure
  
### The program creates a DataFrame with the following columns:
- Ticker: Stock symbol
- Price: Current stock price
- Price-to-Earnings Ratio: P/E ratio
- Number of Shares to Buy: Calculated position sizes

## Usage Example

### Import libraries
import numpy as np
import pandas as pd
import requests
import xlsxwriter
from scipy import stats

### Load stock data
stocks = pd.read_csv('sp_500_stocks.csv')

### Make API calls and build DataFrame
api_url = f'[https://sandbox.iexapis.com/stable/stock/market/batch/?types=quote&symbols=](https://sandbox.iexapis.com/stable/stock/market/batch/?types=quote&symbols=){symbols}&token={IEX_CLOUD_API_TOKEN}'
data = requests.get(api_url).json()

### Filter and rank stocks
final_dataframe = pd.DataFrame(columns=['Ticker', 'Price', 'Price-to-Earnings Ratio', 'Number of Shares to Buy'])

# API Notes
- Uses IEX Cloud's sandbox environment for development
- Processes stocks in batches of 100 for efficiency
- Requires valid API token stored in secrets.py

# Contributing
Pull requests welcome. For major changes, please open an issue first to discuss.

# License
MIT

# Acknowledgments
IEX Cloud for providing market data API
Inspiration from value investing principles
