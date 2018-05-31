# Initial plan of Pikabu rating prediction study


## Cross-sectional research of posts older than a week

### Goal

The goal of the first study is prediction of long-term post ratings

### Step-by-step plan

#### Scrape the site

- Take html of the pages at pikabu.ru/new where the age of posts is greater than 7 days
- Extract post info into features in a dataframe

#### Preprocess features

- Get maximum information from date and time of the publication by using the specified fastai function, comparing dates of publication and op registration, etc.
- Use one-hot encoding for tags and communities
- Create dummies for presence of text, images, videos, links
- Create numeric variables for length of text, number of images, video length, number of tags, length of the title, user rating and number of posts published
- Preprocess text into thematic features

#### Split the data into training, validation and test sets

- In this study I assume that the data are iid, so the split is uniformly random, there are no time series and the goal is not to establish any trends
- The default split ratio is 60:15:25

#### Establish the baseline result with random forest

- Use `sklearn` and `fastai` libraries
- Choose hyperparameters by CV or just on the validation set

#### Try different estimators and compare them with the baseline

- Lasso/Ridge with bootstrap on a dimensionality-reduced set with polynomial features
- SVM on the same/similar dataset
- Gradient descent on a neural network
- Boosting methods

#### Choose the best model

- Choose the loss function
- Check robustness with different loss functions, leaving out some part of the data, common sense checks, error distribution
- Pick one model or several models in different classes and calculate the scores on the test set

#### Interpret results

- Identify the most important features
- Calculate the predicted rating of typical posts to show their advantages and drawbacks
- Formulate the highlights

#### Document the study

- Write a short research paper
- Make an impactful post and publish it

### Notes

- Here I do not study deleted posts. Maybe I will do a deletion-prediction study later
- The data is scraped only once, there is only one data sample for each post
- This study is correlational and not causal, it is not intended to explain why the posts achieve a certain rating, why users vote as they do or why the authors post in a certain manner
- The result does not capture time trends, macrovariable shifts or competing sites, so it is probably going to become outdated soon
