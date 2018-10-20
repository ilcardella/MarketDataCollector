# MarketDataCollector
This is a simple script that request historic price data from AlphaVantage API saving the result in a structured folder tree.
The purpose of this script is to have a process that keeps fetching stocks price data saving it locally.
The script is based on the AlphaVantage project:
https://www.alphavantage.co/


# Dependecies
- Python 3

# Setup
- First you will need to register on the AlphaVantage website requesting a free API key
- Create a file `.api_key` inside the script folder and write the API key inside of it
- You need a file `markets.json` which must contain a list of object that represent the markets you want to collect data of. I have created this file using the IG API but with some minor changes in the script you can just use a simple list of market codes.

# Run
You can run the script manually with
```
python3 MarketDataCollector.py FUNCTION INTERVAL
```
where `FUNCTION` and `INTERVAL` must be replaced according to the AlphaVantage API documentation. See https://www.alphavantage.co/documentation/

A better solution is to setup a cron job (i.e. crontab):
```
crontab -e
```
You can setup the cron job to call the script `market_data_collector` which accept as input argument `start` and `stop`. This will run the script at the market closure every week day:
```
35 16 * * 1-5 /path/to/script/market_data_collector start
```
Remember to define the FUNCTION and INTERVAL inside the shell script!!!

NOTE: You can launch the script with the frequency you prefer, but take into account that depending on the length of the markets list, it might take a while to complete the whole process.
