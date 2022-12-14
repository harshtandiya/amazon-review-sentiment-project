# Amazon Review Sentiment Analysis 
_November 2022_  |  _Harsh Tandiya_

In this project, the idea is to extract the reviews of any amazon product and perform sentiment analysis over it. This can help determine how the customers are feelings 

This project has 2 parts to it:
- Scraping Reviews
- Sentiment Analysis

### 1. Scraping Reviews
The project has a function to scrape the reviews for any required Amazon product. For this, the program requires the ASIN number of the Amazon product. ASIN numbers are unique ID provided by Amazon to each of their products (except the e-books).
ASIN number is usually found in the "Additional Information" section of a product as shown below:
![image](https://user-images.githubusercontent.com/73123690/207691018-f2ddfe19-7ba6-4d0a-b29a-cd85b92eb993.png)

It can also be found in the amazon website url of the product:
![image](https://user-images.githubusercontent.com/73123690/207691093-d8bb0ec6-1862-4147-8b9c-7fe6ecaaece7.png)

We have used **BeautifulSoup** library for pulling out and parsing the HTML & XML data of the webpages. By doing this, we can directly get the review texts from the HTML of the website.
**Requests** module is used to create HTML sessions with the target websites and URLs.
**Pandas** is used throughout the project for performing the standard operations on dataframes.

### 2. Sentiment Analysis

After scraping all the reviews for a particular product and storing it in a .csv or .xlsx format. We read this excel file into a dataframe, and further perform sentiment analysis on this review data that we extracted.

We have performed sentiment analysis by using the pretrained **roBERTa model** by **HuggingFace**. Different _pipelines_ are provided by HuggingFace, that are used in project for accurate sentiment analysis.
The output of this sentiment analysis is then visualized using **seaborn** and **matplotlib** libraries.

## How does it work?
The working of this model is straightforward.
- import the pretrained *Roberta* model to be used.
- model should be given the pretrained twitter sentiment data to learn from.
- Read the excel data that was extracted with teh helo if the *scraper*
- For each review, run it through a scoring function which will perform sentiment analysis on it and give it the respective positive, neutral and negative points along with a 'POSITIVE' or 'NEGATIVE' remark
- Store this review score data in a dataframe, and merge it with the review dataframe with ID as common column
- Remove the inaccurate results, such as 1 star positive review and 5 star negative reviews
- Visualise the remaining data, to show meaningful data
