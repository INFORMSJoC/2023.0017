# Data for replication

Here is the data needed for replicating the experiments. 

## LP 

### Netlib
Netlib instances can be found at https://www.netlib.org/lp/data/index.html.

A off-the-shelf script to download the instances (not up-to-date) can be found at [FirstOrderLp.jl](https://github.com/google-research/FirstOrderLp.jl), under the folder `benchmarking`.

### MIPLIB2017
- benchmark (240 instances): https://miplib.zib.de/tag_benchmark.html
- collection (1065 instances): https://miplib.zib.de/tag_collection.html

### Mittelmann's LP Benchmark
Mittelmann's LP instances are constantly evolving; nevertheless,
one can check the link for [finding primal-dual interior solution](https://plato.asu.edu/ftp/lpfeas.html).

A off-the-shelf script to download the instances (not up-to-date) can be found at [FirstOrderLp.jl](https://github.com/google-research/FirstOrderLp.jl), under the folder `benchmarking`.



## QCP
### LASSO
We use synthetic data for testing Lasso problem, the way to generate the synthetic data can be found in `scripts/bench-qcp/get_lasso_simu_data.m`
### SVM
We choose 6 large SVM instances from [`LIBSVM`](https://www.csie.ntu.edu.tw/~cjlin/libsvm/), namely `covtype`, `ijcnn1`, `news20`, `rcv1_train`, `real-sim`, `skin_nonskin`.
### CBLIB
We benchmark SOCP problems on [`CBLIB`](https://cblib.zib.de) dataset.