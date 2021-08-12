# Hashed Features

### Problem:

Hashed Feature Design Pattern address three problems related to categorical variables in ML
1. When the training vocabulary is incomplete
2. High Cardinality
3. Cold Start problem

### Solution:

The solution is:
1. Convert the categorical input into a unique string
2. Invoke a deterministic and portable hashing algorithm on the string
3. Take the remainder when the hash result is divided by the number of bins. ABS(MOD(FARM_FINGERPRINT(unique_str), NUM_BUCKETS))

### How it solves the problems:

Incomplete Vocab problem, Cold Start --> When a new variable comes in, the hashing algorithm will put it in one of the buckets. It might not be accurate but the model won't error out.

High Cardinality --> We can easily see that we can reduce the cardinality to a number which can easily be reduced.


### Trade Offs:

1. We will bucket different cateogries into one bucket. If one of the categories is highly skewed, then accuracy will drop for the other categories in the bucket.
2. Never use a crypto hash as its not deterministic.

