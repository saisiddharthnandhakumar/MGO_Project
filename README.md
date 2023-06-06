# MGO Customer Ticket Analysis

## Introduction
This was a University Project which I did along with my professor Dr.En Mao who is CAP certified. 

Began with an internship at the company and performed many tasks from 
- Software application testing on Android, ios, and windows
- Form change requests
- UI/UX design 
- Answering customer tickets. 

The issue I was curious about was why MyGovernmentOnline was receiving so many customer tickets over the phone and over feedback forms. 
I was not able to access phone records, but instead got the customer ticket data through the feedback forms.

## Data Collection
I initially wanted to get the customer ticket data from the JIRA rest API. However, when getting the JSON file with all the customer tickets, there seemed to be a problem with their API. Instead I had to manually download all the .csv files. Each file had 10,000 tickets which meant nearly 100 downloads.

## Description Column Cleaning

There were a total of nearly 93967 tickets from 2014 to 2021 out of which only 41751 were actual customer tickets. The remaining being tickets of communications from jurisdictions to the MGO office or sometimes intra-office communication. 

The description column of the csv file was the most important column I needed in order to identify why customers were emailing the company. I had to clean out a most of the data as it contained unncessary tabs, line seperators, https links, and other headers and tails which was not necessary. (This can be seen in the description cleaning jupyter notebook)

## Text Preprocessing
After cleaning the text data, there were some steps to be taken before feeding it into a machine learning model. 
I used **R** to merge all the data from the .csv files together.
Using NLTK, I removed the stop words for less confusion among which words the model has to use, and lemmatized to get root form of the words. 

## EDA (Exploratory Data Analysis)
My initial approach to this project was to just use a deep learning model and to let the model answer all the questions. However, my professor quickly made me understand why that was the wrong approach to solve a problem. 

Below is all my visualizations from my findings. (Also Won the Morris Coats Business Research Award At Nicholls State University)

![research poster](https://i.imgur.com/VuWalyX.png)

## BERTopic 
I went through many options like using OpenAI's GPT-3 for topic identification, using SpaCy for NER or Named Entity Recognition, but could not use OpenAI with uncertainity of the cost of using it and I was not satisfied by my findings using SpaCy.

Finally I came across an article about Topic Modeling and Latent Dirichlet Allocation or LDA. I saw how you could use the BERT language model transformer for topic identification through BERTopic sentance transformers.

After reading through I used UMAP for dimension reduction and HDBScan for the clustering model. 
Tokenization and embedding is done under the hood in BERTopic.

## Recommendations
1. The first recommendation I made (which is in the bottom left of the poster), was a mockup FAQ page I made in order to answer single one word answerable questions. This would save the customers and the cust. representatives a lot time which would usually be wasted in communication over customer tickets.
2. The second was to provide a how-to-do video for tasks which are slightly more complex and require a much more detailed explanation of the steps to be taken
3. Staffing strategies such as providing 4 day work weeks, or half work days, would make the employees much less stressed as the nature of the job is stressful enough. 
