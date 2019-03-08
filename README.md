### Quora_case_study
Quora posted a challenge on Kaggle about how could they better identify whether a question is duplicate or not.

Problem Statement: Given two questions(Q1 & Q2), it has to be determined whether these questions are duplicate of one another.

#### Business Context: 
> If this problem can be solved, Quora can save many man-hours whichit's users will be investing in providing answers to.
> The cost of mis-classification is very high:
  > If the questions are slightly different and are mis-classified as duplicates, it can be extremely costly:
    Because people who come to this question, if they read these answers and realize that these are not relevant to the question, they'll be disappointed and the trust on Quora as an ecosystem where they can get great answers will be lost.
> Hence, what we want is a probability that Q1 is similar to Q2. We can then choose some threshold to decide whether the answers should be merged or not.
> There are no strict latency requirements, i.e. there are no constraint of micro/mili second result. It can take a few seconds to determine this(not hours/days).
> Interpretability is partially important and not fully important. As customer will not ask why/how the answers were merged, but it is important because while designing the algorithm it is important why Q1 & Q2 have been determined to be duplicates or not.

#### Mapping the problem to a Machine Learning Problem
1. Get the data(https://www.kaggle.com/c/quora-question-pairs/data).
2. Get to know the data(this will go throughout the whole project cycle): 
    > Type of data
    > Size of data
    > Rows and columns of data
3. Type of Machine Learning problem to be solved:
    > It is a "Binary Classifiacation" problem for a given pair of questions, it has to be predicted, if they are duplicate or not.
    > Yi ϵ {0,1}
    
⇒ There is a challenge, given Q1 & Q2, we have to featurize the data in such a way that it will be able to help us determine whether Q1 & Q2 are same or not.

#### Performance Matrix
In the business context we understood that we don't want the prediction to be 0 or 1, instead, we want it to be a probability value which lies between 0 & 1.
    > Whenever we have to predict a value in a binary classification setting(although, it can be useful in multi-class classification also), log-loss is one of the best matrix.
    > We will also use binary confusion matrix because we can compute TPR, FPR etc., it gives us a lot more info about what kind of error are occuring.
    
    
#### Splitting the data into train and test
We know that this is a binary classification problem, how sould we split the data for training and then testing.
> The answer is, since we have sufficient amount of data points(~400K), we don't have to worry about the scarcity of data points for any of the purposes. We can do random split in 70:30 or 80:20 train:test ratio. 
