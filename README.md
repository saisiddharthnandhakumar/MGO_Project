# MGO Customer Ticket Analysis
This was a University Project which I did along with my professor Dr.En Mao who is CAP certified. 

The issues I was curious about was why MyGovernmentOnline was receiving so many customer tickets over the phone and over feedback forms. I was not able to access phone records, but instead got the customer ticket data through the feedback forms.

## Description Column Cleaning

There were a total of nearly 93967 tickets from 2014 to 2021 out of which only 41751 were actual customer tickets. The remaining being tickets of communications from jurisdictions to the MGO office or sometimes intra-office communication. 

The description column of the csv file was the most important column I needed in order to identify why customers were emailing the company. I had to clean out a most of the data as it contained unncessary tabs, line seperators, https links, and other headers and tails which was not necessary. (This can be seen in the description cleaning jupyter notebook)

## Text Preprocessing
After cleaning the text data, there were some steps to be taken before feeding it into a machine learning model. 

Using NLTK, I removed the stop words for less confusion among which words the model has to use, and lemmatized to get root form of the words. 

## Initializing BERTopic Model
I went through many options like using OpenAI's GPT-3 for topic identification, using SpaCy for NER or Named Entity Recognition, but could not use OpenAI with uncertainity of the cost of using it and I was not satisfied by my findings using SpaCy.

Finally I came across an article about Topic Modeling and Latent Dirichlet Allocation or LDA. I saw how you could use the BERT language model transformer for topic identification through BERTopic sentance transformers.

After reading through I used UMAP for dimension reduction and HDBScan for the clustering model. 
Tokenization and embedding is done under the hood in BERTopic.
