

Before we can begin our hands-on introduction to data analysis with pandas, we need to learn about the fundamentals of data analysis. Those who have ever looked at the documentation for a software library know how overwhelming it can be if you have no clue what you are looking for. Therefore, it is essential that we not only master the coding aspect, but also the thought process and workflow required to analyze data, which will prove the most useful in augmenting our skill set in the future.

Much like the scientific method, data science has some common workflows that we can follow when we want to conduct an analysis and present the results. The backbone of this process is statistics, which gives us ways to describe our data, make predictions, and also draw conclusions about it. Since prior knowledge of statistics is not a prerequisite, this chapter will give us exposure to the statistical concepts we will use throughout this book, as well as areas for further exploration.

After covering the fundamentals, we will get our Python environment set up for the remainder of this book. Python is a powerful language, and its uses go way beyond data science: building web applications, software, and web scraping, to name a few. In order to work effectively across projects, we need to learn how to make virtual environments, which will isolate each project's dependencies. Finally, we will learn how to work with Jupyter Notebooks in order to follow along with the text.

The following topics will be covered in this chapter:
- The core components of conducting data analysis
- Statistical foundations
- How to set up a Python data science environment


# Fundamentals of Data Analysis

Data analysis is a highly iterative process involving collection, preparation (wrangling), exploratory data analysis (EDA), and drawing conclusions. During an analysis, we will frequently revisit each of these steps. The following diagram depicts a generalized workflow:

![[Screenshot 2023-11-15 at 00.13.20.png]]

In practice, this process is heavily skewed towards the data preparation side. Surveys have found that, although data scientists enjoy the data preparation side of their job the least, it makes up $80 \%$ of their work (https://www. forbes.com/sites/gilpress/ 2016/03/23/data-preparation-most-time-consuming-least-enjoyable-datascience-task-survey-says/\#419ce7b36f63). This data preparation step is where pandas really shines.

## Data Collection

Data collection is the natural first step for any data analysis - we can't analyze data we don't have. In reality, our analysis can begin even before we have the data: when we decide what we want to investigate or analyze, we have to think of what kind of data we can collect that will be useful for our analysis. While data can come from anywhere, we will explore the following sources throughout this book:

- Web scraping to extract data from a website's HTML (often with Python packages such as selenium, requests, scrapy, and beautifulsoup)
- Application Programming Interfaces (APIs) for web services from which we can collect data with the requests package
- Databases (data can be extracted with SQL or another database-querying language)
- Internet resources that provide data for download, such as government websites or Yahoo! Finance
- Log files

Chapter 2, Working with Pandas DataFrames, will give us the skills we need to work with the aforementioned data sources. Chapter 12, The Road Ahead, provides countless resources for finding data sources.

We are surrounded by data, so the possibilities are limitless. It is important, however, to make sure that we are collecting data that will help us draw conclusions. For example, if we are trying to determine if hot chocolate sales are higher when the temperature is lower, we should collect data on the amount of hot chocolate sold and the temperatures each day. While it might be interesting to see how far people traveled to get the hot chocolate, it's not relevant to our analysis.
Don't worry too much about finding the perfect data before beginning an analysis. Odds are, there will always be something we want to add/remove from the initial dataset, reformat, merge with other data, or change in some way. This is where data wrangling comes into play.


## Data Wrangling

Data wrangling is the process of preparing the data and getting it into a format that can be used for analysis. The unfortunate reality of data is that it is often dirty, meaning that it requires cleaning (preparation) before it can be used. The following are some issues we may encounter with our data:
- Human errors: Data is recorded (or even collected) incorrectly, such as putting 100 instead of 1000 , or typos. In addition, there may be multiple versions of the same entry recorded, such as New York City, NYC, and nyc
- Computer error: Perhaps we weren't recording entries for a while (missing data)
- Unexpected values: Maybe whoever was recording the data decided to use ? for a missing value in a numeric column, so now all the entries in the column will be treated as text instead of numeric values
- Incomplete information: Think of a survey with optional questions; not everyone will answer them, so we have missing data, but not due to computer or human error
- Resolution: The data may have been collected per second, while we need hourly data for our analysis
- Relevance of the fields: Often, data is collected or generated as a product of some process rather than explicitly for our analysis. In order to get it to a usable state, we will have to clean it up
- Format of the data: The data may be recorded in a format that isn't conducive to analysis, which will require that we reshape it
- Misconfigurations in data-recording process: Data coming from sources such as misconfigured trackers and/or webhooks may be missing fields or passing them in the wrong order

Most of these data quality issues can be remedied, but some cannot, such as when the data is collected daily and we need it on an hourly resolution. It is our responsibility to carefully examine our data and to handle any issues, so that our analysis doesn't get distorted. We will cover this process in depth in Chapter 3, Data Wrangling with Pandas, and Chapter 4, Aggregating Pandas DataFrames.