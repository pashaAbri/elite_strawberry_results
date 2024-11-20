# Classification Distribution Analysis

The analysis shows how well our experiment's dataset sample represents the full Davidson dataset distribution. The
output compares the distribution of classifications (Hate Speech, Offensive Language, and Neither) between our processed
experiment samples and the complete dataset. Each class shows both the raw count and percentage representation in our
experiment versus the full dataset. The representation analysis further breaks down what percentage of each classification type we've processed (
e.g., "10.5% of all Hate Speech examples"), helping verify our experiment's coverage across different categories. This
analysis is crucial for ensuring our experiment results aren't skewed by sampling bias and that we're working with a
representative subset of the data.

## Distribution Results

### Classification Distribution Comparison

```
Classification         Processed            Full Dataset           
----------------------------------------------------------------------
Hate Speech           67 (  6.2%)          1430 (  5.8%)
Offensive Language    825 ( 76.4%)         19190 ( 77.4%)
Neither              188 ( 17.4%)          4163 ( 16.8%)
----------------------------------------------------------------------
Totals               1080 (100.0%)         24783 (100.0%)


Hate Speech representation:        4.7% (67/1430)
Offensive Language representation: 4.3% (825/19190)
Neither representation:           4.5% (188/4163)

Overall dataset representation:    4.4% (1080/24783)
```
