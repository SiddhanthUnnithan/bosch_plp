# bosch_plp
Bosch Production Line Performance Analysis

https://www.kaggle.com/c/bosch-production-line-performance

- Refer to analysis.txt for notes taken while 'modelling'

Submission Deadline
- Friday, November 11th

Evaluation
- Matthews correlation coefficient (MCC)
- MCC = ((TP * TN) - (FP * FN))/sqrt((TP+FP) * (TP+FN) * (TN+FP) * (TN+FN))
- TP = true positives; TN = true negatives; FP = false positives; FN = false negatives
- define MCC and compute each case after running against test

Submission
- Id, response
- Id = part id; response = binary failure 

Problem
- binary classification
- predict which parts will fail quality control based on part features

Business Model Understanding
- bosch manufactures hundreds of thousands of parts at a high frequency
- defective parts cost the same amount as functional parts, in terms of manufacturing
- losses are incurred when defective parts are used and shipped to end user
        - forms: refunds, free-exchanges, lawsuits
- two possible forms of prediction:
        - right after manufacturing => defective parts are discarded
        - while manufacturing; after particular steps => non-trivial

Data Model
- 968 numeric features
- 1,183,747 unique parts => expecting computations on the entire dataframe to be slow
- 6879 TP recorded failures 
