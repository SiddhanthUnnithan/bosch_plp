# Bosch Production Line Performance Analysis

Preliminary classifier for continuous features related to production line, with precision score of 89.2% (low number of false failures classified).

## Notebook
https://siddhanthunnithan.github.io/bosch_plp/

Refer to analysis.txt for notes taken while modelling.

## Competition Details
https://www.kaggle.com/c/bosch-production-line-performance

### Evaluation
- Matthews correlation coefficient (MCC)
- MCC = ((TP * TN) - (FP * FN))/sqrt((TP+FP) * (TP+FN) * (TN+FP) * (TN+FN))



### Business Model Understanding
- bosch manufactures hundreds of thousands of parts at a high frequency
- defective parts cost the same amount as functional parts, in terms of manufacturing
- losses are incurred when defective parts are used and shipped to end user
        - forms: refunds, free-exchanges, lawsuits
- two possible forms of prediction:
        - right after manufacturing => defective parts are discarded
        - while manufacturing; after particular steps => non-trivial

### Data
- 968 numeric features
- 1,183,747 unique parts
- 6879 TP recorded failures 
