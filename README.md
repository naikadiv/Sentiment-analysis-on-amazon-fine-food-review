# Title :
#A Comprehensive Evaluation of GloVe, Word2Vec, and Custom Embeddings for Sentiment Analysis of Amazon Fine Food Reviews
# Introduction: 
Everyday we come across various products in our lives, on the digital medium we swipe across hundreds of product choices under one category. It will be tedious for the customer to make selection. Here comes 'reviews' where customers who have already got that product leave a rating after using them and brief their experience by giving reviews. As we know ratings can be easily sorted and judged whether a product is good or bad. But when it comes to sentence reviews we need to read through every line to make sure the review conveys a positive or negative sense. In the era of artificial intelligence, things like that have got easy with the Natural Langauge Processing(NLP) technology.
# Data Set requirements: 
Amazon Fine Food Reviews dataset is used. The dataset contains 568,454 food reviews Amazon users left up to October 2012 https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews 
Glove embedding file -https://www.kaggle.com/datasets/yasheshtiwari/glove6b100dtxt
# Objective:
 This project contains the code for Sentiments Analysis applied on the Amazon Fine Food Reviews Dataset. The model facilitates classification of a Food review into a positive or a negative review. We explore multiple approaches to text representation and sentiment classification Multiple approaches used: Model 1: Custom Embedding Model 2: Word2Vec Embedding Model 3: GloVe Embedding + Averaging Model 4: GloVe Embedding + Advanced Architecture
# Preprocessing: 
The preprocessing steps applied to the text in this model include the following: Text Normalization: All text was converted to lowercase to ensure consistency and avoid treating words like "Apple" and "apple" as different entities. HTML Tag Removal: Any HTML tags present in the reviews were removed to clean the text further. Special Character Removal: All special characters were eliminated, retaining only English letters (a-z), digits (0-9), and periods (.). Stopword Removal: Commonly used words that do not contribute to sentiment, such as "the," "and," and "of," were removed. Lemmatization: Words were reduced to their base or root form using lemmatization (e.g., "studying" was converted to "study"). Review Length Filtering: Analysis of the dataset revealed that over 70% of reviews contained fewer than 60 words. Therefore, reviews exceeding 60 words were excluded to streamline the training data. Dataset Splitting: The cleaned dataset was split into training, validation, and testing sets in a 60:20:20 ratio. Tokenization and Padding: Words in the reviews were converted into numerical indices through tokenization. Reviews with fewer than 60 words were padded with zeroes to maintain a consistent length across the dataset. These preprocessing steps ensure the text is clean, uniform, and ready for training on NLP models.
# Model Implementation: 
Four models were used for training :

1.Custom Embedding Model : In this model, the Custom Word Embeddings Layer is used as the first layer in the model i.e. no pre-trained embeddings were used. Instead, the model learnt the word embeddings for the first layer on its own. Training Accuracy - 99.14% Validation Accuracy - 94.86% Test Accuracy - 94.92%

2.Word2Vec Model : In this model, the Word Embeddings were first learnt using the Gensim Word2Vec model. After the embeddings were learnt, they were given as fixed untrainable input to the model as the first layer. Training Accuracy - 93.21% Validation Accuracy - 93.72% Test Accuracy - 93.89%

3.Averaging Model : In this model, pre-trained 100-dimensional GloVe Embeddings (i.e. glove.6B.100d) were used. For each word in the review, the corresponding GloVe word embedding was extracted which was then averaged out for the whole review. The final averaged embedding was then used as an input to the model. This model did not take into account the relative positioning of words as they were just being averaged out. Training Accuracy - 90.27% Validation Accuracy - 89.42% Test Accuracy - 89.38%

4.GloVe Model : This model is exactly similiar to the 2nd model except for the difference that fixed pre-trained untrainable 100-dimensional GloVe Embeddings (i.e. glove.6B.100d) were used instead of Word2Vec embeddings. Training Accuracy - 92.92% Validation Accuracy - 93.38% Test Accuracy - 93.13%
The First and Second Model are Sentiment_analysis_1.ipynb file. The Third and Fourth Model are implemented in Sentiment_analysis_2.ipynb file.
# KeyInsights: 
The first model, the Custom Embeddings Model, clearly outperformed all other models and achieved the highest accuracy on the test set. The Word2Vec Model ranked second in performance, followed by the GloVe Embeddings Model in third place. The Averaging Model demonstrated the lowest test accuracy among all models, which was expected as it employed a basic approach that did not account for the relative positioning of words in the reviews.
# Sample Classifications:
This is how the best model out of all four i.e. Custom Embeddings Model classified the following self-written reviews :

"The taste of the biscuits was quite spectacular. It seemed as if it was taken straight from heaven"

Result : Positive with 99.64% surity

"Peanuts were too salty according to my taste"

Result : Negative with 99.84% surity

"Food was unhygienic. I fell ill after eating"

Result : Negative with 96.88% surity

"I am sure I liked what i had"

Result : Positive with 66.48% surity

"I am not sure I liked what i had"

Result : Negative with 99.47% surity

"If you are looking for a secret ingredient, go for it"

Result : Positive with 88.35% surity

"When i first bought this, i was confused about its quality and taste. But after eating this, my children fell in love with me. Thanks!!"

Result : Positive with 99.54% surity

"If you are looking for a quality food, dr. oetkers product always seem to be my first choice"
Result : Positive with 94.34% surity

"I'm not really a tea drinker but my husband is and he loves this tea. So on his behalf I'm recommending it. Just go on with my hubby's recommendation."

Result : Positive with 96.55% surity
