# Introduction 
This Project delivers the need Kubernetes Definitions to deploy Simpifier on a Kubernetes Cluster.
This is a step by step guidance, no automation

based on https://github.com/simplifier-ag/docker-compose/tree/release/8.1


# Current running setup
1. Create config, namespace, secret examples etc.
```shell
kubectl apply -f ./config/config.yaml 
```

2. Create database service
```shell
kubectl apply -f ./mysql/mysql-deployment.yaml
```

3. Create databases with Job, wait for the finished job
```shell
kubectl apply -f ./mysql/mysql-init-deployment.yaml
```

4. Create Simplifier
```shell
kubectl apply -f ./simplifier/simplifier-deployment.yaml
```

```shell
kubectl apply -f ./simplifier/simplifier-launchpad.yaml
```

```shell
kubectl apply -f ./simplifier/simplifier-designtime.yaml
```

```shell
kubectl apply -f ./simplifier/simplifier-runtime.yaml
```


5. Setup Ingress Routes, based on https://github.com/simplifier-ag/docker-compose/blob/release/8.1/docker-compose.yml
```shell
kubectl apply -f ./kyma/istio.yaml
```