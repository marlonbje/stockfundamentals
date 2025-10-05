# StockInfo

This project provides a Python class `StockInfo` to fetch, store, analyze, and visualize financial data for a list of stock tickers using the `yfinance` library.

## Features

- **Automatic financial data retrieval** (Free Cash Flow, Total Revenue, Net Income, EPS)
- **Quarterly or yearly data support**
- **Caching of fetched data to CSV files**
- **Earnings visualization**
- **Growth analysis with margins and revenue trends**
- **Industry diversification pie chart**
- **Statistical summary with CAGR, volatility, efficiency, and Sharpe ratio**

## Requirements

Make sure you have the following Python packages installed:

```bash
pip install pandas numpy yfinance plotly
```

## File Input

Create a `.txt` file with one stock ticker per line, e.g.:

```
AAPL
MSFT
GOOGL
```

## Usage

```python
from your_script import StockInfo

# Example (quarterly mode):
obj = StockInfo('DJI.txt', 'q')
obj.plot_earnings()
obj.plot_growth()
obj.plot_diversification()
obj.print_statistics()
```

- Use `'q'` for quarterly data.
- Use `'y'` for yearly data.

The script automatically saves fetched financials to:
```
{TICKER}_financials-{frequency}.csv
```

## Methods Overview

### `get_data()`
Fetches or loads data for each stock and stores it in CSV files.

### `get_industry()`
Retrieves the industry classification for each ticker using `yfinance`.

### `plot_earnings()`
Visualizes EPS estimates vs actuals (only for quarterly data).

### `plot_growth()`
Displays FCF margin, net margin, and revenue changes across periods.

### `plot_diversification()`
Creates a donut chart of portfolio diversification by industry.

### `print_statistics()`
Calculates and prints:
- CAGR
- Average Net Growth
- Volatility
- Cash Efficiency
- Sharpe Ratio (custom formula)

## Running as Script

The script ends with:

```python
if __name__ == '__main__':
    obj = StockInfo('DJI.txt','q')
    obj.plot_earnings()
    obj.plot_growth()
    obj.plot_diversification()
    obj.print_statistics()
```

Modify `'DJI.txt'` and frequency as needed.

## Notes

- Invalid tickers are automatically skipped.
- Rate limiting (`time.sleep`) is included to avoid API throttling.
- Missing or invalid data may produce NaN in statistics.
