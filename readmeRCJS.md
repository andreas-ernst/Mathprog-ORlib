# Resource Constrained Job Scheduling (RCJS) datasets

**Files:** [RCJS_Instances.zip](data/RCJS_Instances.zip) and [RCJS_new_instances.zip](data/RCJS_new_instances.zip)

These data files contain instances for a problem where jobs need to be scheduled on a set of machines with the following characteristics:
* Jobs have a given fixed assignment to machines
* The machines are linked by a single shared resource constraint which all jobs consume while they are running
* Each job has a release time, a due date, and is potentially linked to other jobs by precedence constraints 
* The objective is to minimise the weighted tardiness.

There are two collections of instances with the newer instances generated to provide more challenging examples as the solution algorithms for these problems have improved.

The data sets have been used in a number of papers, including:
* Singh, G., & Ernst, A. T. (2011). [Resource constraint scheduling with a fractional shared resource](https://www.sciencedirect.com/science/article/pii/S0167637711000575). Operations Research Letters, 39(5), 363-368.
* Nguyen, S., Thiruvady, D., Ernst, A. T., & Alahakoon, D. (2019). [A hybrid differential evolution algorithm with column generation for resource constrained job scheduling](https://www.sciencedirect.com/science/article/pii/S0305054819301224). Computers & Operations Research, 109, 273-287.
* Blum, C., Thiruvady, D., Ernst, A. T., Horn, M., & Raidl, G. R. (2019). [A Biased Random Key Genetic Algorithm with Rollout Evaluations for the Resource Constraint Job Scheduling Problem](https://link.springer.com/chapter/10.1007/978-3-030-35288-2_44). In Australasian Joint Conference on Artificial Intelligence (pp. 549-560). Springer, Cham.
* Nguyen, S., & Thiruvady, D. (2020, July). [Evolving Large Reusable Multi-pass Heuristics for Resource Constrained Job Scheduling](https://ieeexplore.ieee.org/abstract/document/9185539/). In 2020 IEEE Congress on Evolutionary Computation (CEC) (pp. 1-8). IEEE.
 
The data files may contain comments starting with `//` and contain the following information in the given order:
* Number of machines
* Resource limit (max power available)
* For each machine:
    * number of jobs on machines n_k
    * One line per job with tab separated fields:
        `id release_time  proc_time due_time  power_required  weight`
* Dependencies (precedences):
    * Number of precedences
    * One line per precedence with index of jobs i and j such that i precedes j (jobs numbered from 1)

***Note:*** the zip file for the "new" instances contains a python script to generate instances. The filenames of these instances indicate how they were generated:

> `RCJS_<seed>_<machine>_<power factor>_<edge probability>`

 
