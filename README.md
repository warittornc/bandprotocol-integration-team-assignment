# Assignment - Band Protocol's Integration Team

## About the assignment

Your task is to create a package that is able to get the median prices for each the symbols given while removing any
outliers.

## Before you get started

### Core requirements

The package must be able to do the following features:

- The main function must accept a list of symbols and return a list of the corresponding prices in USD or an error.
- Must be able to calculate the median price of each symbol.
- The code must be able to handle errors for symbols that aren't supported by the exchanges.
- The code must filter out symbols does not have at least three sources out of the given five.
- The code must filter out the prices that are outliers. The method for filtering the outliers is up to your discretion.
- The code must not use the outlier prices during calculations.

### Assignment rules

The only allowed imports are those that are built directly into the
[Python Standard Library](https://docs.python.org/3/library/) and the [requests](https://pypi.org/project/requests/)
library.

### Expected folder structure

You should design the code similar to how you would design a package. An example folder structure can be seen below:

    ...
    ├── band_assignment
    │   ├── handler                 # Contain the API handlers
    │   │   ├── __init__.py 
    │   │   ├── binance.py          # API handler for Binance
    │   │   ├── coingecko.py        # API handler for CoinGecko
    │   │   ├── coinmarketcap.py    # API handler for CoinMarketCap
    │   │   ├── kraken.py           # API handler for Kraken
    │   │   ├── okx.py              # API handler for OKX
    │   │   └── wrapper.py          # wrapper function to call all API handlers
    │   │ 
    │   ├── calculator              # Contains any modules that requires calculations
    │   │   ├── __init__.py
    │   │   └── ...
    │   │ 
    │   ├── structs                 # Contains custom structs/errors if any
    │   │   ├── __init__.py
    │   │   ├── errors              # Contains custom errors if any
    │   │   └── ...
    │   │
    │   └── main.py                 # Contains the main function to run
    │
    ├── tests                       # Contains test scripts
    │   └── demo.py                 # Demo script for using the package
    │   └── tests.py                # unit-tests [Optional]
    │   └── conftest.py             # conftest file [Optional]
    │    
    └── README.md                   # Contains the final report

### Get familiar with the APIs

The API that are to be used and its corresponding documentations are given below:

- [Binance](https://binance-docs.github.io/apidocs/spot/en/#change-log)
- [CoinGecko](https://www.coingecko.com/en/api/documentation)
- [CoinMarketCap](https://coinmarketcap.com/api/documentation/v1/)
- [Kraken](https://docs.kraken.com/rest/)
- [OKX](https://www.okx.com/docs-v5/)

Please be aware you will need to create an account for CoinMarketCap in order to get an API key

## Core functionality

### Handler functions

#### Example function

```python
def get_exchange_prices(symbols: List[str]) -> List[Optional[float]]:
    # Insert logic here
    return prices
```

#### Example results

if the following code is run:

```python
if __name__ == "__main__":
    exchange_prices = get_exchange_prices(["BTC", "ETH", "NOTAREALTOKEN"])
```

`exchange_prices` should be returned in a format equivalent to this:

```python
exchange_prices = [23541.0, 1532.32, None]
```

### Calculator functions

#### Example function

```python
def filter_outliers(prices: List[float]):
    # Insert logic here
    return filtered_prices


def get_median_price(filtered_prices: List[float]):
    # Insert logic here
    return median_price
```

#### Example results

If the following code is run:

```python
if __name__ == "__main__":
    prices_list = [
        [10.0, 10.1, 9.8, 1000],
        [200.1, 200.1, 200.8, 0.9],
    ]
    median_prices = []
    for prices in prices_list:
        filtered_prices = filter_outliers(prices)
        median_prices.append(get_median_price(filtered_prices))
```

`filtered_prices` and `median_prices` should be in a format equivalent to this:

```python
# Loop 1
filtered_price = [10.0, 10.1, 9.8]
median_prices = [10.0]
# Loop 2 
filtered_price = [200.1, 200.1, 200.8]
median_prices = [10.0, 200.1]
```

### Main function

#### Example function

```python
def get_prices(symbols: List[str]) -> Dict[str, Optional[float]]:
    # Insert logic here
    return prices
```

#### Example results

If the following code is run:

```python
if __name__ == "__main__":
    results = get_prices(["BTC", "ETH", "NOTAREALTOKEN"])
```

`results` should be returned in a format equivalent to this:

```python
results = {
    "BTC": 23541.0,
    "ETH": 1532.32,
    "NOTAREALTOKEN": None,
}
```

### Test cases

The test cases can be found in the `test_cases.json` file in this repository

### What we expect from you

1. Think about how the code should be structured, follow [PEP 8](https://peps.python.org/pep-0008/) guidelines and use
   type hinting via the [typing](https://docs.python.org/3/library/typing.html) library.
2. Consider factors such as API rate limit/weights and coding efficiency when designing your solution.
3. Include a demo in the demo.py file that showcases the results from the test cases.
4. In the README.md, document all the technical decisions and trade-offs you've made, why you made those decisions or
   trade-offs, the specific outlier rejection method you've used and why you chose that method and any other feature
   you've left out that you would implement if given more time.

### Optional task

For bonus points, you can write a set of unit tests. Make sure to think of the possible edge cases and create a conftest
file to simulate the handler functions

## Need help?

If you have any doubts, questions or would like to request an extension, feel free to contact us at any time. You can
reach us at talent@bandprotocol.com or through posting an issue in this repository.

# bandprotocol-integration-team-assignment
