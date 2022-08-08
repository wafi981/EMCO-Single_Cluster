# Single Cluster Example



## Changing config files

/home/ubuntu/work/emco-base/examples/single-cluster

nano config

HOST_IP=localhost

KUBE_PATH=/home/ubuntu/.kube/config

DNS=true



## Run the script 

```
./setup.sh create

```
Output files of this command are:

- values.yaml: specifies useful variables for the creation of EMCO resources

- emco_cfg.yaml: defines the deployment details of EMCO (IP addresses and ports of each service)

- prerequisites.yaml: defines all non usecase-specific EMCO resources to create

Helm charts and profile tarballs for all the usecases.



## Applying prerequisites to run tests

Apply prerequisites.yaml. This is required for all the tests. This creates controllers, one project, one cluster, a logical cloud. This step is required to be done only once for all usecases:

```
emcoctl --config emco-cfg.yaml apply -f prerequisites.yaml -v values.yaml

```



## Instantiating Logical Cloud over the cluster

```
emcoctl --config emco-cfg.yaml apply -f instantiate-lc.yaml -v values.yaml
```



## Running test cases

Prometheus and collectd usecase

```
emcoctl --config emco-cfg.yaml apply -f test-prometheus-collectd-deployment.yaml -v values.yaml
emcoctl --config emco-cfg.yaml apply -f test-prometheus-collectd-instantiate.yaml -v values.yaml
```

