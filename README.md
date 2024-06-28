# FilingDatesScraper

Get the filing dates for a company.

---

### Setup

1. Clone git repository: `https://github.com/PrimalFinance/FilingDatesScraper.git`
1. Configure the "config.json" file.

```
    {
        "chrome_driver_path": "D:\\PATH TO CHROME DRIVER\\chromedriver.exe",
        "data_export_path": "D:\\PATH TO EXPORT DATA"
    }

```

3. Install the projects requirements with `pip install -r requirements.txt`

---

### Instructions

- In this example we will be using **NVDA** as an example.
- Create a class instance.

```
   fd = FilingDates("NVDA", alpha_vantage_key=alpha_vantage_key)
```

###### Get Filing Dates

- Gets the period end from Q1 to Q4

```
    fd.get_filing_dates()

    # Output
            Q1     Q2     Q3     Q4 fiscal_end
    ticker
    NVDA    04-30  07-31  10-31  01-31      01-28
```

###### Local Data

- The program will first try to access information locally from `filing_dates.csv`.
- Below is the format that the data is saved in.

```
    ~filing_dates.csv:

        ticker,Q1,Q2,Q3,Q4,fiscal_end
    AMZN,03-31,06-30,09-30,12-31,12-31
    CHPT,04-30,07-31,10-31,01-31,01-31
    MSFT,09-30,12-31,03-31,06-30,06-30
    AAPL,12-31,03-31,06-30,09-24,09-24
    AVAV,07-29,10-29,01-28,04-30,04-30
    KTOS,03-31,06-30,09-30,12-31,12-25
    META,03-31,06-30,09-30,12-31,12-31
    SMR,03-31,06-30,09-30,12-31,12-31
```

- Adding to local storage will look like this.
- The function `get_filing_dates()` will automatically save data to `filing_dates.csv`.

```
    fd = FilingDates("ORCL", alpha_vantage_key=alpha_vantage_key)
    fd.get_filing_dates()

    ~filing_dates.csv:

        ticker,Q1,Q2,Q3,Q4,fiscal_end
    AMZN,03-31,06-30,09-30,12-31,12-31
    CHPT,04-30,07-31,10-31,01-31,01-31
    MSFT,09-30,12-31,03-31,06-30,06-30
    AAPL,12-31,03-31,06-30,09-24,09-24
    AVAV,07-29,10-29,01-28,04-30,04-30
    KTOS,03-31,06-30,09-30,12-31,12-25
    META,03-31,06-30,09-30,12-31,12-31
    SMR,03-31,06-30,09-30,12-31,12-31
    ORCL,08-31,11-30,02-28,05-31,05-31  <-----------

```
