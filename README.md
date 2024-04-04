# lions-den-hackathon-2024
a repository containing the solution of the PŁiwo team for the Lion's Den 2024 hackathon, organized by ING. 

# the challenge 

The challenge was based on developing an EWS (Early Warning System) for a bank. The system is supposed to show, based on selected parameters, how likely a given client of the bank is to not pay their debt (e.g. a loan). The (16) teams working on the problem had 8 hours (16:00 - 00:00) to develop their solutions. In the next section, I describe our team's approach.   

# the data

The contestants were given two datasets: an *in-time* one and an *out-of-time* one (train and test ones, respectively), each containing 300 features and roughly 310000 training examples. An important data-related constraint was that the final model of choice could only take 9 of the 300 features as inputs. Some of the features were presented month-wise,  

Some of the issues to be dealt with are outlined below:

- Class imbalance (roughly 90% of the training samples had the *target* parameter equal to 0)
- Missing values (some of the parameters had less than a couple percent of non-corrupted samples)
- Poorly aggregated features

# our solution

For selecting the 9 most important features, we mainly relied on the *SelectKBest* algorithm from the SciKit-Learn Python library. Because of an insufficient amount of time, no meaningful EDA could be conducted. 

Our predictive model of choice was *RandomForests* from the TensorFlow Python framework, because of its interpretability in a business/banking context, reliability and inherent ability to deal with imbalanced classification. 

## feature engineering 

Our feature engineering procedure mainly consisted of dropping redundant (e.g. highly corrupted/irrelevant datetime) features and aggregating those features that should have been summarized into one and were presented as several features quantifying the same parameter for each month instead. 

# SUBMITTED model performance

On the feature-engineered train, test sets the model had 94.5% and 90.4% accuracy, respectively. 

# TODO

Validate the model (ROC, AUC curves, cross-validation, confusion, cost matrices etc), describe + improve the feature engineering procedure, clean up and document the code.

## CHANGELOG
- 04.04.2024 -- added the base model, updated readme 
