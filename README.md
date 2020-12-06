
## LSTM predict stock market


# 1. Setup Data file path structute.

Collecting data from financial-data
Need to install `setuptools` by bash script through Ubuntu/or Python environment. Simply install setuptool using the command:

* For Ubuntu users:
`sudo apt-get install -y python-setuptools`

* For Python3:
`sudo apt-get install -y python3-setuptools`
After that, install your `package` again normally, using:
`sudo python setup.py install`
That's all !

Then you can run that script below, examples:

```from setuptools import setup, find_packages

setup(
    name = 'pyfinancialdata', 
    version = '0.2',
    author = 'XYZ',
    author_email = 'IMEI3007@gmail.com',
    license = 'GPLv3', 
    description = 'Intraday financial data files for backtesting or analysis', 
    package_data = {
         'pyfinancialdata': [
            'data/crypytocurrencies/*/*/*/*csv', 
            'data/currencies/*/*/*/*.csv', 
            'dat/stocks/*/*/*.csv'
          ],
    },
    packages = [
         'pyfinancialdata',
    ], 
    install_requires = [
          'pandas'
    ],
    classifiers = [
         'Environment :: Console',
         'Operating System :: POSIX',
         'Programming Language :: Python :: 3 :: Only'
     ],
 )
 ```
     
Intraday financial data files for backtesting or analysis. Currently this includes minutes bars for:

* In Histdata

- S&P 500 from 2010-2018 in USD (SPXUSD) 
- NIKKEI 225 from 22010-2018 in JYP (JPXJPY) 
- DAX 30 from 2010-2018 in EUR (GRXEUR) 
- EUROSTOXX 50 from 2010-2019 in EUR (ETXEUR) 

* In Oanda ( that wrapper for working with Oanda Account)
- Currencies pairs 2005-2020: `AUD_JPY, AUD_USD, EUR_USD, GPB_USD, USD_CAD` (from  Oanda) 
This package will parse the CSV files and return them as a [`Pandas DataFrame`]
Pull requests welcome.

# Data file path structure

`data/<type>/<provide>/<instrument>`
That include 3 main folder as: `cryptocurrencies`, `currencies`, `stocks`

In fact, the data flow is illustrated:

* With cryptocurrencies:
`data/cryptocurrencies/bistamp/BTC_USD/2012.csv`
`data/cryptocurrencies/kraken/BTC_EUR/2018.csv`
* With currencies:
`data/currencies/oandaAU200_AUD/2005/oanda-AU200_AUD_2005-1.csv`
* With stocks:
`data/stocks/histdata/ETXEUR/DAT_ASCII_ETXEUR_M1_2010.csv`  

Stock data for the S&P 500 index from the histdata provider
### Examples 
#####_*BTC_*

```python
import pyfinancialdata
data = pyfinancialdata.get(provider='bitstamp', instrument='BTC_USD', year=2017)
data.tail(3)
                     open      high       low     close     price
date
2017-12-31 23:57:00  13908.73  13913.26  13874.99  13913.26  13913.26
2017-12-31 23:58:00  13913.26  13953.83  13884.69  13953.77  13953.77
2017-12-31 23:59:00  13913.28  13913.28  13867.18  13880.00  13880.00
```
####_*S&P 500*_

```python
import pyfinancialdata
data = pyfinancialdata.get(provider='histdata', instrument='SPXUSD', year=2017)
data.tail(3)
                        open     high      low    close    price
date
2017-12-29 16:55:00  2668.75  2668.75  2668.00  2668.25  2668.25
2017-12-29 16:57:00  2667.75  2668.50  2667.75  2668.00  2668.00
2017-12-29 16:58:00  2668.25  2668.50  2667.75  2668.50  2668.50
```
####_*ER.USD*_

```python
import pyfinancialdata
data = pyfinancialdata.get(provider='oanda', instrument='EUR_USD', year=2017)
data.tail(3)
                       close     high      low     open  volume    price
date
2017-12-29 21:57:00  1.20045  1.20071  1.20004  1.20018      50  1.20045
2017-12-29 21:58:00  1.20041  1.20041  1.20041  1.20041       1  1.20041
2017-12-29 21:59:00  1.20039  1.20039  1.19970  1.20036      14  1.20039
```
### Optinal time grouping for longer timeframes
You can set time_group = `60min`, time_group = `1day`
As well as setting by each year or group years by `get_multi_year` detain on code:
Look back to `Initialize Bollinger Bands Indicator`

```
provider = ['kraken', 'bitstamp', 'oanda', 'histdata']
instrument = 'SPXUSD'
years = [2016, 2017, 2018]
time_group = '10min'

def get_multi_year(provider, instrument, years, time_group):
        year_dfs = []
        
      for year in years:
        year_dfs.append(
           get(
              provider = provider, 
              instrument = instrument, 
              year = year, 
              time_group = time_group
             )
           )  
      return ....
      ```
      
              
   


