# bosch_plp
Bosch Production Line Performance Analysis

Problem
- binary classification
- predict which parts will fail quality control based on part features

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
