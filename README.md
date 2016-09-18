# bosch_plp
Bosch Production Line Performance Analysis

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

Notes
- data represents part measurements
- large number of anonymized features
- can group features based on production and station lines
        - L<prod line>_S<station line>_F<feature id>
- three main feature types: numerical, categorical, date
        - date: timestamp for when measurement was taken
        - n features
        - i_th date column corresponds to i-1_th feature where iE[1, n+1]
        - assuming sequential relation between measurements and dates
        - (e.g. x measurements => x dates => 1 column in train_date.csv)

Strategy
- analyze each feature set separately
- numerical patterns (i.e. direct pattern between numerical features)
        - is there an identifiable correlation between a numeric feature and classification tag
- unsure of categorical significance, need more research
- combine feature sets and identify relationship between types
