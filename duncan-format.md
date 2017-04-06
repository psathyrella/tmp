
## partition information

Use a single column in a csv to describe a partition of the entire data set.
This column consists of semi-colon separated clusters.
Each cluster consists of colon-separated sequence ids.
Each row in the csv contains a different partition.
For instance a line for the best partition, but also lines for somewhat more inclusive clusters to communicate the clustering uncertainty.

For example, if we have five sequences labeled `a` through `e`, we could represent a single partition as:

```
partitions
e:d;a:b;c
```

For multiple partitions, and adding a column for log probability:

```
partitions,logprob
e:d;a:b;c,-200.3
e:d:a:b;c,-210.7
e:d:a:b:c,-530.1
```

## annotation information

The clustering/partition csv above would be a different file than the [annotation csv](https://github.com/airr-community/airr-formats/blob/master/docs/rearrangements.md) which we've already discussed/decided on.
A concept that we need to be able to represent in these files is the annotation of a cluster of sequences.
For example, the inferred n-insertion for `a` by itself will be in general different than for if we assume that `a` and `b` are clonal.
I have two proposals to handle this simultaneous annotation of multiple sequences

#### option 1: generalize the existing annotation csv

We can take the [annotation csv](https://github.com/airr-community/airr-formats/blob/master/docs/rearrangements.md) and generalize the columns to handle more than one sequence.
For instance, the `id` column would allow multiple colon-separated ids, like `a:b` for two sequences with ids `a` and `b`.

#### option 2: put annotation information in the partition csv

ok, actually, I don't see a neat way to do this, but maybe someone else will.
