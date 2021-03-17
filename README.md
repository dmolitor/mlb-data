# MLB Transaction Data

This repo houses [MLB Transaction Data](http://mlb.mlb.com/mlb/transactions/) from January, 2001 to the beginning of the current month. 
This data is in structured .csv format, with columns ```transaction``` (specifying which team did which action with which player(s)) and 
```date``` (specifying the date of the given transaction).

## Importing the Data

If you want all this data available locally, simply clone the repository and you should be set. Alternatively you can import this data directly from Github.
Below are two short helper functions for importing the data in both R and Python.

- **R**
```r
read_transactions <- function(year = "all-years") {
  # Base URL
  github_raw <- "https://raw.githubusercontent.com/dmolitor/mlb-transaction-data/main/"
  # Append particular year
  transactions_url <- paste0(github_raw, year, "/transactions.csv")
  # Import data using readr
  readr::read_csv(transactions_url)
}

# Import all transactions for 2007
transactions_2007 <- read_transactions(year = 2007)

# Import all transactions
transactions_all <- read_transactions()
```

- **Python**
```python
import pandas as pd

def read_transactions(year = "all-years"):
  # Base URL
  github_raw = "https://raw.githubusercontent.com/dmolitor/mlb-transaction-data/main/"
  # Append particular year
  transactions_url = github_raw + str(year) + "/transactions.csv"
  # Import data using pandas
  dat = pd.read_csv(transactions_url)
  return dat

# Import all transactions for 2007
transactions_2007 = read_transactions(year = 2007)

# Import all transactions
transactions_all = read_transactions()
```

## Issues with the Data

On several random baseball forums I've seen people complaining about the quality of MLB's Transaction data. I'm sure this complaining is warranted. As such,
if there are mistakes or missing records, feel free to open an issue or pull request and fix this data!
