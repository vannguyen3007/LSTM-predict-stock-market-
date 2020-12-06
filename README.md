
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

`from setuptools import setup, find_packages

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
 )`    
     
Intraday financial data files for backtesting or analysis. Currently this includes minutes bars for:

* In Histdata

- S&P 500 from 2010-2018 in USD (SPXUSD) 
- NIKKEI 225 from 22010-2018 in JYP (JPXJPY) 
- DAX 30 from 2010-2018 in EUR (GRXEUR) 
- EUROSTOXX 50 from 2010-2019 in EUR (ETXEUR) 

* In Oanda ( that wrapper for working with Oanda Account)
- Currencies pairs 2005-2020: `AUD_JPY, AUD_USD, EUR_USD, GPB_USD, USD_CAD` 


