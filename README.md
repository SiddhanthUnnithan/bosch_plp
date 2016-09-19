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
- 968 numeric features
- 1,183,747 unique parts
        - expecting computations on the entire dataframe to be slow
- 6879 TP recorded failures
- 

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

Numerical Training Set
- need to identify relationships between features
- we can discard n-1 features if n features are numerically related (direct mapping)
- one of the easiest ways to view the relationship between features is to generate plots
        - problem: 970 x 970 grid of plots (will take a while to compute)
        - we can split it into chunks and view smaller sets at each time
- can start by separating different types
        - only two distinct types: 'float64' and 'int64' where 'int64' has 2 counts
        - int64 counts: Id, Response (not useful)
- (Sep 18) might have to come back to numerical set => too large
- group features based on line and station
        - there seems to be only four lines (0, 1, 2, 3)
        - line 0: 24 stations, 168 features
        - line 1: 2 stations, 513 features
        - line 2: 3 stations, 42 features
        - line 3: 21 stations, 245 features
- start with analysis of line 2 => 3 dataframes
        - smallest number of features
        - might give indication of how useful it is to segment the data based on line and station
        - dataframe identification df_0<station number>
- analysis of line 0 => 24 dataframes
        - look at all 
        - dataframe identifcation df_0<station number>
        - df_226
                - nothing unusual in terms of value counts for each column
