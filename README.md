# Bitcoin-Minute-Momentum-Study
to investigate if bitcoin has momentum using minute OHLCV data
### Data Description
bitstampUSD_1-min_data_2019-01-01_to_2019-06-30.csv: Bitcoin data at 1-min intervals from bitstamp exchanges, from 2019-01-01 to 2019-06-30
#### Field
* Timestamp: Start time of time window (60s window), in utc format
* Open: Open price at start time window
* High: High price within time window
* Low: Low price within time window
* Close: Close price at end of time window
* Volume_(BTC): Amount of BTC transacted in time window
* Volume_(Currency): Amount of Currency transacted in time window
* Weighted_Price: volume-weighted average price (VWAP)
#### Additional Data Processing on Raw Data (not included in the repository, following codes FYI only)
Raw Data Source (https://www.kaggle.com/mczielinski/bitcoin-historical-data/version/17#)
* convert utc timestamp to utc format
* slice the data to only include the period from 2019-01-01 to 2019-06-30 (due to GitHub 25 MB file size limit)
```python
import pandas as pd
import datetime
btc_data = pd.read_csv('bitstampUSD_1-min_data_2012-01-01_to_2019-08-12.csv', index_col='Timestamp')
btc_data.index = [datetime.datetime.utcfromtimestamp(ts) for ts in btc_data.index]
btc_data.index.name = 'Timestamp'
btc_data['2019-01-01 00:00:00':'2019-06-30 23:59:59'].to_csv('bitstampUSD_1-min_data_2019-01-01_to_2019-06-30.csv')
```
