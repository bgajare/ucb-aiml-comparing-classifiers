# ucb-aiml-comparing-classifiers

CRISP-DM stages were used to solve this problem and build models. Below is the analysis for each step.

## Business understanding 
Given the data from a bank that tracked the phone calls made to its targetted customers, we want to predict if the customer will actually do a long term deposit. 
While at the same time see if such a campaign is actually useful of the resources it consumes, as such campaings are generally harder to implement as the costs
of labor might be quite high. 

## Data Understanding 
The provided data seemed rather clean with hardly any cleaning to be done. Though in the colab, I did remove one column and retried all the models, but this did
not amount to significant boost in performance.
It is to be noted that the data is quite imbalanced with 11.2% yes and 88.8% no.

## Data Preparation 
As part of data preparation, label encoders were used to encode the string target variable to a integer, StandardScaler was used for numerical columns and
one-hot-encoding was used for categorical columns. After all the transformations, the dataset contained over 4K samples and 63 features. 

## Modelling 
First created a basic "Always No" model, which will basically always predict a No. Since the No vales are 88.8% in our data, this basic models accuracy
is thus 88.8%. Any model we create further should be better than this baseline. 
Then the below models were trained 
1. Logistic Regression
2. k-nearest neighbors
3. Decision Tree Classifiers
4. Support Vector Machines

Also performed a GridSearch on the hyperparameters for k-nearest neighbors and Decision Tree classifiers.

## Evaluation 
The dataset was split into 80% for training and 20% for testing / cross validation. 
All models pretty much behaved the same, with roughly 91% training accuracy and 89 - 92% test accuracy
It was notable that the DecisionTreeClassifier had a training accuracy of 100% and a test accuracy of 89%, which indicates overfitting.

## Deployment 
1. We cannot really accurately predict the target given this data, if accurate data is desired, then there should be more balance in the data.
2. If this imbalance in the data is inherent naturs of the business problem, then in opinion of this analysis, such a marketing camapaign isn't
   very effective. Though for a complete understanding of how effective this campaign is depends on outcomes of other campaigns and ideas (if any)
