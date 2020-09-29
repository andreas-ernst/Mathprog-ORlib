The Indonesia Container Distribution (ICD) dataset 
==================================================

> By Wira Redi, Hamid Mokhtar, Mohan Krishnamoorthy, and Andreas T.
> Ernst; Nov 25th, 2017

**File:** [ICD_dataset.zip](data/ICD_dataset.zip) see also [ICD Computational Results](data/ICD_ComputationalResults_csv.zip)

Directories 
-----------

The main directory is *ICD.* It contains original instances. The other
directories contain modified version of the orignial instances to either
include more rail links, or consider a discount factor for usage of rail
links in the problem input.

    <ICD>               The set of original instances 
    <ICD10xtra>         The set of instances with 10% more rail links than the original ones
    <ICD25xtra>         The set of instances with 25% more rail links than the original ones
    <ICD66prcnt>        The set of instances whose rail transfer costs are discounted by 66%
    <ICD99prcnt>        The set of instances whose rail transfer costs are discounted by 99%

Files
-----

Each directory contains the Indonesian Container Distribution network
design datasets. The format of each file is as below:

-   file name: `<n>.<h>.<p>.<q>` - data file for \<n\> nodes,
    \<h\> potential hubs, \<p\> number of hubs, and \<q\> minimum number
    of rail terminals.

-   file name: Fcost\<n\>.\<h\> - data file for fixed costs and
    intermodal change costs corresponding to \<n\>.\<h\>.\<p\>.\<q\> for
    all \<p\> and \<q\>.

-   genInstances.py: Use this python code script to generate more
    instances. Basically, using input file, it generates other possible
    instances with different \<p\> and \<q\>, while \<n\> and \<h\>
    remains unchanged. Output files will be writen in the same folder as
    the input.

### Generate instances {#generateinstances}

usage: (run in shell script)

     $ python genInstances.py DIRECTORY 

For example, run `python genInstances.py ICD`

### 

Instance format: \<n\>.\<h\>.\<p\>.\<q\>

    <n>                   Number of nodes including potential hubs  
    <a>                           Number of arcs  
    <m>                           Number of modes
    <h>                           Number of potential hubs
    <p>                           Number of hubs
    <q>                           Minimum number of rail hubs
    <c1> <c2> <c3>            Cost factors for modes 1,...,m  {m= 1 for sea,m=2 for road,m=3 for rail}
    <s>                           Number of potential inland hubs
    <S1> ... <Ss>               Potential inland hubs  
    <i_1> <j_1> <d_1> <m_1>         Travel distance (in meter) <d_t> from <i_t> to <j_t> with mode <m_t> 
      :
      :
    <i_a> <j_a> <d_a> <m_a>                    
    <w[1][1]> <w[1][2]> ... <w[1][n-h]>            flow from the first O/D node to all others
      :         :             :
      :         :             :
    <w[n-h][1]> <w[n-h][2]> ... <w[n-h][n-h]>      flow from n-h demand nodes to all others

### Fcost\<n\>.\<h\> {#fcostnh}

    <F_1>                               The fixed cost of potential hub <1>
    <F_2>
    .
    .
    .
    <F_h>
    G<1,2>  G<1,3>                         G<k,l>  is the change-mode cost factor from mode k to mode l at a seaport
    G<2,1>  G<2,3>  G'<2,3>                G'<k,l> is the change-mode cost factor from mode k to mode l at an inland hub
    G<3,1>  G<3,2>  G'<3,2>           
