# ECBS+ML

This is the code base for ECBS+ML.
It applies ML to learn node-selection strategies for ECBS. 

## Installation 
The code requires the external library: BOOST (https://www.boost.org/).

One also needs to fit your own cmake version, current version in CMakeList.txt is 3.16.5 (2.8.12 is also suitable).

### To compile the code:
```
mkdir build
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
make
```

### To run the code:
```
# for running a single instance
./build/ECBS -m [PATH_TO_MAP] -a [PATH_TO_SCEN] -n [NumberOfAgents] -o [OutputFIle] -t [TimeLimit] -w [FocalWeight] -b [MergeThreshold] -s [MODE] -i [StartAgentIDForScenFile] --debug [true/false] --maecbs [true/false]
```



## Required Inputs:

  -m [ --map ]        : Input file for map (*string*)
  
  -a [ --agents ]     : Input file for agents (*string*)

  -n [ --agentNum ]   : Number of agents (*int*)
  
  -o [ --output ]     : Output file for schedule (*string*)

  -s [ --solver ]     : Solver to use (*int*, 0: EPEA\*, 1: CBS, 2: ECBS, 3: MA-CBS(EPEA\*), 4: MA-CBS(CBS), 5: MA-ECBS, 6: MA-ECBS(EPEA\*), 7: MA-ECBS(CBS), 8: Evaluate path.txt)
 
 ## Optional Inputs:

  -w [ --weight ]     : Suboptimal bound for ECBS (*float*, default: 1.00)
  
  -t [ --cutoffTime ] : Cutoff time (seconds) (*int*, default: 300)

  --rt                : Times to restart randomly under cutoff time. This is triggered by time. (*int*, default: 0)

  --seed              : Random seed (*int*, default: 0)

  --debug             : Debug mode (*int*, 0: Nothing, 1: Print all output, 2: Print HL and LL nodes, default: 0)
  
  --help              : Produce help message
