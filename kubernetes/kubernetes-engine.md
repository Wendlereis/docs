# Getting started with Google Kubernetes Engine (GKE)

## Creating a Kubernetes Engine cluster

```
$ gcloud container clusters create [CLUSTER-NAME]
```
```
NAME        LOCATION       MASTER_VERSION  MASTER_IP      MACHINE_TYPE   NODE_VERSION   NUM_NODES  STATUS
my-cluster  us-central1-a  1.12.8-gke.10   35.188.57.214  n1-standard-1  1.12.8-gke.10  3          RUNNING
```

## Getting the cluster's credentials

```
$ gcloud container clusters get-credentials [CLUSTER-NAME]
````

## Deploying an application to the cluster

```
$ kubectl run hello-server --image=gcr.io/google-samples/hello-app:1.0 --port 8080

$ kubectl expose deployment hello-server --type="LoadBalancer"
```
> Passing in type="LoadBalancer" creates a Compute Engine load balancer for your container.

## Debugging

```
$ kubectl get service hello-server
```

## Delete a cluster

```
$ gcloud container clusters delete [CLUSTER-NAME]
```

[<< Menu](../README.md)