# YahooFinanceScraper

This is a python class for interfacing with Yahoo Finance API for basic stock data. Add this file to existing projects and import the scraper to use built in functions.

### Functions:
- getCurrPrice(stock): returns current price of a stock ticker 
- getExpirationDates(stock): returns avaliable expiration dates (in Unix time) for option contracts of a stock ticker
- getContracts(stock, expiration, optionType): returns all avaliable option contracts of a given stock. Raises value error if none found. 
  - stock = ticker symbol
  - expiration = expiration date in Unix time (use 12:00am time of date)
  - optionType = 'calls' or 'puts'
- getPutPrice(stock, expiration, strike) - Returns premium of PUT option contrac. Raises value error if no contract found. 
  - stock = ticker symbol 
  - expiration = expiration date in Unix time (use 12:00am time of date)
  - strike = desired strike price of the option
- getCallPrice(stock, expiration, strike) - same interface as getPutPrice() but for CALL options

*See additional endpoints for yahoo finance API here (post by Ryder Brooks): https://stackoverflow.com/questions/44030983/yahoo-finance-url-not-working

### Example Usage
    import yahooFinanceScraper as yf

    scraper = yf.YahooFinanceScraper()

    # get current price of SPY
    currPrice = scraper.getCurrPrice('SPY')  

    # get premium for a SPY call option at strike price of 375 expiring on 12/14/2020
    call = scraper.getCallPrice('SPY', 1607904000, 375)   
    
      
### Libraries Used:
- requests - HTTP requests on APIs
- Yahoo Finance API - scraping options data
- time/datetime - custom timer for determing option contract expiration dates

  
