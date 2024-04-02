[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# An Enhanced ADMM-based Interior Point Method for Linear and Conic Optimization

This archive is distributed in association with the [INFORMS Journal on Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](https://github.com/INFORMSJoC/2022.0372/blob/master/LICENSE).

The software and data in this repository are a snapshot of the software and data that were used in the research reported on in the paper [An Enhanced ADMM-based Interior Point Method for Linear and Conic Optimization](https://doi.org/10.1287/ijoc.2023.0017) by Qi Deng, Qing Feng, Wenzhi Gao, Dongdong Ge, Bo Jiang, Yuntian Jiang, Jingsong Liu, Tianhao Liu, Chenyu Xue, Yinyu Ye and Chuwen Zhang.

## Cite

To cite the contents of this repository, please cite both the paper and this repo, using their respective DOIs.

https://doi.org/10.1287/ijoc.2023.0017

https://doi.org/10.1287/ijoc.2023.0017.cd

Below is the BibTex for citing this snapshot of the respoitory.

```
@article{deng2023new,
  title  =    {New Developments of ADMM-based Interior Point Methods for Linear Programming and Conic Programming}, 
  author =    {Qi Deng and Qing Feng and Wenzhi Gao and Dongdong Ge and Bo Jiang and Yuntian Jiang and Jingsong Liu and Tianhao Liu and Chenyu Xue and Yinyu Ye and Chuwen Zhang},
  publisher = {INFORMS Journal on Computing},
  year =      {2024},
  doi =       {10.1287/ijoc.2023.0017.cd},
  url =       {https://github.com/INFORMSJoC/2023.0017},
  note =      {Available for download at https://github.com/INFORMSJoC/2023.0017},
}  
```

## Description

ADMM-based Interior Point Method for Linear and Conic Programming **(ABIP)** is a new framework that applies alternating direction method of multipliers (ADMM) to implement interior point method (IPM) for solving large-scale linear programs (LP) and conic programs (QCP).

ABIP (LP part) was initially developed by **[Tianyi Lin (https://github.com/tyDLin)](https://github.com/tyDLin)** and is currently maintained by **[LEAVES](https://github.com/leavesgrp)** optimization software platform. 

The original ABIP follows the following paper:

```
@article{lin_admm-based_2021,
	title = {An {ADMM}-based interior-point method for large-scale linear programming},
	volume = {36},
	number = {2-3},
	journal = {Optimization Methods and Software},
	author = {Lin, Tianyi and Ma, Shiqian and Ye, Yinyu and Zhang, Shuzhong},
	year = {2021},
	note = {Publisher: Taylor \& Francis},
	pages = {389--424},
}
```

### Version
Current version of ABIP is 2.0

### Installation

We provide the Matlab interface. The C interface is planned for 3.0 release.
To install ABIP, install [`Intel OneAPI MKL`](https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#base-kit) first.

We suggest that the user set the environment variables by using the script provided by OneAPI.
It is typically located at `path-to-oneapi/setvars.sh`.

For example, on Ubuntu, the root path of OneAPI is `/opt/intel/oneapi`, then you can run the following,

```bash
cd to_the_root_directory_of_abip
source /opt/intel/oneapi/setvars.sh       
``` 

When you finish the setups, use `install.m` script in the root directory


## Basic Usage

### Basic usages for ABIP-LP

ABIP operates on  the standard form LP, i.e.,

$$
\begin{aligned}
\min ~ &c^Tx \\
\text{s.t.} ~&Ax = b\\
&x\ge 0
\end{aligned}
$$

and accepts standard `sedumi` format defined using $A, b, c, K$.

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


For convenience, we provide scripts to proceed the standard form LP, reformulates the problem to the appropriate format, see [Replicating](#replicating).

### Basic usages of ABIP-QCP

ABIP operates on the following quadratic cone programming (QCP), i.e.,

$$
\begin{aligned}
\min ~ &\frac{1}{2}x^TQx + c^Tx \\
\text{s.t.} ~&Ax = b\\
&x\in \mathcal{K}
\end{aligned}
$$

where $Q \in \mathbb{S}_{+}^n, c \in \mathbb{R}^n, b \in \mathbb{R}^m, A \in \mathbb{R}^{m \times n}$, and $\mathcal{K}$ is a closed convex cone.

To call it, use

```
[x, y, s, info] = abip(data, K, params)
```
ABIP-QCP shares most of the parameters with ABIP-LP, except for the convex cone K, currently we support following cones:
|   Parameter   | Explanation                                            |
| :-----------: | :----------------------------------------------------- |
|    K.q    | array of second-order cone constraints                                    |
|   K.rq   | array of rotated second-order cone constraints       |
|      K.f      | length of free cone     |
| K.z | length of zero cone                                |
| K.l  | length of LP cone                                  |

**Note**: columns of data matrix A must be specified in the order above.

## Results

The result files can be found in `results`

## Replicating

To replicate the results in the paper, please refer to the README [here](scripts/README.md)

## Ongoing Development

This code is being developed on an on-going basis at the author's
[Github site](https://github.com/leavesgrp/ABIP).

## Support

For support in using this software, submit an
[issue](https://github.com/leavesgrp/ABIP/issues/new).

## License

### Main License

Licensed under the MIT License (see `LICENSE` file).

### External Dependencies

All located in `src/external/`:

- **AMD (SuiteSparse)**: BSD. Freely used under BSD terms.
- **LDL & CSparse (SuiteSparse)**: GNU LGPL. Modifications must remain under LGPL.
- **QDLDL (OSQP)**: Apache License 2.0. Modifications should be noted.

### Contributions

Contributions are licensed under the project's MIT license. Review individual licenses in `src/external/` for compliance.


---

This README section is provided for informational purposes only and does not constitute legal advice. If you have any questions or concerns about the licensing terms or compliance, especially regarding third-party dependencies, please consult with a legal expert.
