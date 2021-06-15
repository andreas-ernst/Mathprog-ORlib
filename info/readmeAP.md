Commonly used data sets for hub location problems include:

* The _Civil Aeronautics Board (CAB)_ instances are due to Prof.
  Morton E. O'Kelly and are mirrored here for convenience (see below)
* The _Australia Post (AP)_ instances (see below)
* The _Turkish Network_ (TR) instances are available from Prof Bahar
     Yetis Kara at this
     [webstite](https://ie.bilkent.edu.tr/~bkara/hub_location.php)
* Less commonly used but much larger, the _USA423_ data set by 
  J. Peiró, A. Corberán A. and R. Martí (see
  [UrApHMP](http://www.optsicom.es/uraphmp/)). For convenience this
  instance has been mirrored [here](../data/USA423data.zip)

------------------------------------------------------------------------
Australia Post (AP) dataset for p-hub median and capacitated hub location problems
==================================================================================

**File:** [APdata.zip](../data/APdata.zip)

The Australia Post data set was first published in:

* Ernst, Andreas T., and Mohan Krishnamoorthy. "[Efficient algorithms
  for the uncapacitated single allocation p-hub median problem](https://www.sciencedirect.com/science/article/pii/S0966834996000113)"
  Location science 4, no. 3 (1996): 139-154.
* Ernst, Andreas T., and Mohan Krishnamoorthy. "[Solution algorithms
  for the capacitated single allocation hub location problem](https://doi.org/10.1023/A:1018994432663)" Annals
  of Operations Research 86 (1999): 141-159. (With capacities & fixed costs)

This download contains the AP (Australia Post) data set for p-hub median and capacitated hub location problems. The files contain the following:

* APdata200 - Data file for a full 200 node problem with 8 hubs
* generate.c - C program for generating smaller data sets
  
   >   USAGE: generate n p <APdata200> newdata
   
  This creates a new problem with n nodes and p hubs
* 20.3 - A sample data set with 20 nodes produced by
   >   generate 20 3 <APdata200> 20
* FcostX.NN - Fixed cost file for NN nodes where X = \'T\' or \'L\' (the T problems tend to be more difficult). Fcost files are not relevant to the p-hub location problems
* CapY.NN - Node capacity file for NN nodes where Y = \'T\' or \'L\' (the T problems are more tightly constraint) . Capacity files are not
relevant to the p-hub location problems
* Solutions-*.txt - Optimal solutions for all combinations of capacitated (CSAHLP) and uncapacitated single allocation (USApHMP) and multiple allocation (UMApHMP) hub median problems, with n in {10,20,25,40,50} and multiple options for hubs or capacities. In the result files we use the nomenclature "NNXY" to refer to the problem generatedfrom data files NN, FcostX.NN and CapY.NN. The objective is given as well as the allocation of hubs. Eg an allocation vector 2,2,4,4,4 means that nodes 2 & 4 are hubs, node 1 is allocated to hub node 2 and nodes 3 & 5 to hub
node 4.

Data file format for nodes file:
```
<n>                         Number of nodes
<x[1]> <y[1]>               x & y coordinates of node 1
:
:
<x[n]> <y[n]>               x & y coordinates of node n
<w[1][1]> <w[1][2]> ... <w[1][n]>    flow from node 1 to all others
: : :
: : :
<w[n][1]> <w[n][2]> ... <w[n][n]>    flow from node n to all others
<p>        Number of hubs (for p-hub median problems)
<δ>        Collection cost
<α>        Transfer cost
<χ>        Distribution cost
```

All of the costs are per unit (euclidean) distance, per unit flow
volume.

The costs and and capacity files contain one number for each node (in the same order as in the nodes file). For FcostX.NN this represents the cost of making the node a hub. For CapY.NN the numbers are the capacity on incoming commodities (including from the node itself) if that node is
made a hub.

------------------------------------------------------------------------
Civil Aeronautics Board (CAB) Hub Location Instances
==================================================================================


This is really just a 25 node instance with smaller instances created
by taking the first n nodes (typically for n=10,15 & 20) and by
varrying the transfer cost (typically 0.2 to 1.0 in steps of 0.2).
These instances have been contributed to the research community by M.E. O'Kelly.

This is the 25 node data set that has been
used extensively with hub and spoke location models. It is
sometimes referred to as the CAB data set. Full references
to the source and prior results for these data can be found
in several previous paper, including 

1. O'Kelly, Morton E. "[A quadratic integer program for the location of
   interacting hub facilities.](https://www.sciencedirect.com/science/article/pii/S0377221787800073)" _European Journal of Operational
   Research_ 32, no. 3 (1987): 393-404.
2. O'Kelly, Morton E., Deborah Bryan, Darko Skorin-Kapov, and Jadranka
   Skorin-Kapov. "[Hub network design with single and multiple allocation:
   A computational study](https://www.sciencedirect.com/science/article/pii/S0966834996000150)" _Location Science_ 4, no. 3 (1996): 125-138. 

This data is provided in two formats

* `25.3.4`  - same format as the AP data sets
* `CAB25.txt` - number of nodes, n x n matrix of flow (w), n x n
  matrix of distances
  
  
**File:** [CABdata.zip](../data/CABdata.zip)
