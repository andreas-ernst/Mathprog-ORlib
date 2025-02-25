# Degree Constrained Minimum Spanning Tree (DCMST) dataset

**File:** [dcmst.zip](../data/dcmst.zip)

The DCMST problem is to find a minimum cost spanning tree on a graph in which each node has at most a maximum degree d. The DCMST data available here has been used in the following papers:

* Ernst, A. T. (2010). [A hybrid Lagrangian particle swarm optimization algorithm for the degree-constrained minimum spanning tree problem](https://doi.org/10.1109/CEC.2010.5585939). In _IEEE Congress on Evolutionary Computation_ (pp. 1-8). IEEE.
* Krishnamoorthy, M., Ernst, A. T., & Sharaiha, Y. M. (2001). [Comparison of algorithms for the degree constrained minimum spanning tree](https://doi.org/10.1023/A:1011977126230). _Journal of Heuristics_, 7(6), 587-611.


The CRD and SYM data sets have been obtained from Anton Volgenant, the remainder
have been created by Andreas Ernst and Mohan Krishnamoorthy.

## Format:
The CRD files contain simply co-ordinates in a 2-dimensional euclidean space (truncate to integer). All others contain 1/2 of the symmetric
cost matrix between all pairs of points. These should be read with a loop
of the form:

```python
  for i=1..n:
    for j=1..i-1:
      distance[i,j] = distance[j,i] = read_next_number;
```

Note that the number of nodes, n, is given by the file name (the first two
digits, with the last digit being the instance number). The only exception is
that the 100 node data sets are 10x for x=0..9

There are 126 such data files in [dcmst.zip](../data/dcmst.zip)

## Other files:

* **Data generators:** the .c files contain data generators for different types of data sets. Use at your own risk.
* `bestSolutions.txt`: list of best known solutions to go with the 2001 paper on DCMST written by Ernst, Krishnamoorthy & Sharaiha
