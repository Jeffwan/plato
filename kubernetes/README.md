# Plato on Kubernetes guidance

## Prerequiste

You need to follow the instructions to build plato successully. 


## Build container image

```
# specify context to root folder
docker build -t seedjeffwan/plato:latest -f kubernetes/Dockerfile .
```

## Launch a Kubernetes cluster

You can either use AWS EKS or GCP GKE.

```
gcloud config set compute/zone us-west1-a

gcloud container clusters create plato \
  --scopes=gke-default \
  --num-nodes=2 \
  --no-enable-autoupgrade \
  --machine-type=e2-standard-4
```

## Install mpi-operator

```
git clone https://github.com/kubeflow/mpi-operator
cd mpi-operator
kubectl create -f deploy/v1alpha2/mpi-operator.yaml
```

## Launch a Job

```
kubectl apply -f pagerank_job.yaml
```
