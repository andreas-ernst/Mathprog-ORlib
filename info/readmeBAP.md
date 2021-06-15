# Berth Allocation Problem (BAP) dataset

**File:** [BAP-Data.zip](../data/BAP-Data.zip)

Test data for the paper 

> Ernst, Andreas T., Ceyda Oğuz, Gaurav Singh, and Gita Taherkhani. "Mathematical models for the berth allocation problem in dry bulk terminals." _Journal of Scheduling_ 20, no. 5 (2017): 459-473.

For details of the problem and benchmark solution information please refer to the above paper.

 

Problems are defined in terms of

* A - Arrival time of each vessel (hours since start of planning period)
* P - Processing time for the vessel (hours)
* L - Length of the vessel
* B - Beginning of each tidal window
* E - End of each tidal window

The folder of data sets in `inputData/` contains

- `.xlsx` files: each parameter is in a separate sheet, with 10 instances in 10 columns
- `.dat` files: for use with OPL studio files for running the integer programming solution method
- `.csv` files: simpler text format files with each vector of data on one line
 

In addition the OPL studio source code used for the paper is provided in `.mod` files

 
There are 900 instances however only 400 have been converted into csv format. 
 
