# Changing config files

/home/ubuntu/work/emco-base/examples/single-cluster

nano config

HOST_IP=localhost

KUBE_PATH=/home/ubuntu/.kube/config


# Run the script 

```
./setup.sh create

```
Output files of this command are:

- values.yaml: specifies useful variables for the creation of EMCO resources

- emco_cfg.yaml: defines the deployment details of EMCO (IP addresses and ports of each service)

- prerequisites.yaml: defines all non usecase-specific EMCO resources to create

Helm charts and profile tarballs for all the usecases.

# Next step
```
emcoctl --config emco-cfg.yaml apply -f prerequisites.yaml -v values.yaml

```
