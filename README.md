[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

## ABIP
### ADMM-based Interior Point Method for Linear and Conic Programming

ABIP is a new framework that applies alternating direction method of multipliers (ADMM) to implement interior point method (IPM) for solving large-scale linear programs (LP) and conic programs (QCP).

ABIP(LP) was initially developed by **[Tianyi Lin (https://github.com/tyDLin)](https://github.com/tyDLin)** and is currently maintained by **[LEAVES](https://leaves.shufe.edu.cn)**  optimization software platform. 

### Version
Current version of ABIP is 2.0

### Reference

- Lin, Tianyi, et al. "An ADMM-based interior-point method for large-scale linear programming." Optimization Methods and Software (2020): 1-36.
- Deng, Qi, et al. "New Developments of ADMM-based Interior Point Methods for Linear Programming and Conic Programming." *arXiv preprint arXiv:2209.01793* (2022).

### Installation

We provide the Matlab interface. The C interface is planned for 3.0 release.
To install ABIP, install [`Intel OneAPI MKL`](https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#base-kit) first.

We suggest that the user set the environment variables by using the script provided by OneAPI.
It is typically located at `path-to-oneapi/setvars.sh`.

For example, on Ubuntu, the root path of OneAPI is `/opt/intel/oneapi`, then you can run the following,

```bash
source /opt/intel/oneapi/setvars.sh       
``` 

When you finish the setups, use `install.m` script in the main direction.

### Basic usages of ABIP

ABIP accepts standard sedumi format defined using $A, b, c, K$.

To call it, use

```
[x, y, s, info] = abip(data, K, params)
```

|   Parameter   | Explanation                                            |
| :-----------: | :----------------------------------------------------- |
|    verbose    | If log is turned on                                    |
|   normalize   | Whether to perform data scaling before the solve       |
|      pcg      | Whether to use iterative solver for linear systems     |
| max_admm_iter | Maximum ADMM iteration                                 |
| max_ipm_iter  | Maximum IPM iteration                                  |
|   timelimit   | Time limit                                             |
|      tol      | Relative tolerance of convergence                      |
|    solver     | Choose which solver to use, -1: automatic 1: force QCP |


## Results


## Replicating

To replicate the results in the paper, please refer to the README [here](scripts/README.md)

## Ongoing Development

This code is being developed on an on-going basis at the author's
[Github site](https://github.com/leavesgrp/ABIP).

## Support

For support in using this software, submit an
[issue](https://github.com/leavesgrp/ABIP/issues/new).
