The multiple depot vehicle scheduling problem (MDVSP) dataset
=============================================================

###  By Sarang Kulkarni, Mohan Krishnamoorthy, Abhiram Ranade, Andreas Ernst, and Rahul Patil; Jan 2018

**File:** [MDVSP.zip](../data/MDVSP.zip)

The directory contains sixty instances of the MDVSP. Each instance file is named as `RN-m-n-k`.dat, denoting the k'th
instance involving `m` depots and `n` trips.
Each instance contains following information:
1. `m` - number of depots
2. `n` - number of trips
3. `l` - number of locations
4. `v_i` - the maximum number of vehicles in depot `i = {1,...,m}`
5. Trip information of each trip i: start time (`s_i`), start location (`p_i`), end time (`e_i`), and end location (`q_i`)
6. Travel matrix: Time to travel between any two locations `l_i` to `l_j`: `d(l_i,l_j)`
   Note: Locations are numbered from 0 to l-1. Locations `{0,...,m-1}` are depot-locations (locations of depots) and locations `{m,...,l-1}` are trip-locations(where trips start/end).

Format of each instance is as follows:

* first line: `m\ n\ l`
* second line: m entries, one for each `v_i,\ i = {1,...,m}`
* Next n lines contain the trip information.
Line for `i^{th}` trip: `s_i\ p_i\ e_i\ q_i`
* Next l lines provide the travel matrix: Each entry in i^th row and j^th column provide travel time between location `l_i` and `l_j`, `d(l_i,l_j)`.


Various costs in different formulations are calculated as follows:

1. The multi-commodity network flow formulation (MCNF):
   * Pull-out cost from depot i to trip `j = 5000 + 10 * d(l_i,p_j)`.
   * Pull-in cost from trip j to depot `i = 5000 + 10 * d(q_j,l_i).`
   * Connection from trip i to trip j is feasible if `s_j \ge e_i +
d(q_i,p_j),` and 
   * connection cost is given by: `8 * d(q_i,p_j) + 2 * (s_j,e_i)`.

2. The time-space network flow formulation (TSNF):
   Each node j represents location (l_j) at time (t_j). Location for depot i is represented as `l_i`. The start-time (`t_0`) of planning horizon is zero, and end-time (`t_e`) is calculated as `\max(q_1,...,q_n) + 10`.

   * The pull-out cost from node i to node j, where node i represents depot-location i at t_0 and node j represents trip-location j at time `t_j = 5000 + 10 * d(l_i,l_j).` The pull-in cost from node i to node j, where node i represents depot-location i at `t_e` and node j represents trip-location j at time `t_j = 5000 + 10 * d(l_j,l_i).`
   * The deadheading cost from location node j to node k, where node j represents trip-location `l_j` at time `t_j` and node k represents trip-location l_k at time `t_k = 8 * d(l_j,l_k) + 2 * (t_k - t_j)`. Note that deadheading is possible if `t_k \ge t_j + d(l_j,l_k).`
   * The waiting cost from node j to node j+1 that represent the same trip-location l_j at time t_j and `t_{j+1}`, respectively `= 2 * (t_{j+1} - t_j)`.


3. The inventory formulation: 
   Each node j represents location (`l_j`) at time (`t_j`). Location for depot i is represented as l_i. The start-time (`t_0`) of planning horizon is zero, and end-time (`t_e`) is
calculated as `\max(q_1,...,q_n) + 10`.
   * The pull-in arc from node j to node i, where node j represents
trip-location l_j at time t_j and node i represents depot-location `l_i`
at `t_e = 5000 * 10 d(l_j,l_i).`
   * The cost of the inventory arc that starts from depot-location `l_i` at t_0
to end of trip j at node `(q_j,e_j) = 5000 * 10 d(l_i,q_j).`
   * The cost of the inventory arc that starts from trip-location l_j at t_j
to end of trip k at node `(q_k,e_k) = 8 * d(l_j,p_k) + 2 * (s_k - t_j)`. 
     Note that the inventory arc is feasible if `s_k \ge t_j + d(l_j,p_k).`
   * The waiting cost from node j to node j+1 that represent the same
trip-location l_j at time t_j and `t_{j+1}`, respectively `= 2 * (t_{j+1} - t_j)`.


Use C++ file `GenerateInstances.cpp` to generate new instances.
> Usage: ./GenerateInstances m n k

where m - number of depots, n - number of trips, and k - number of
instances to be generated.

 

 

 

 

 

 

 
