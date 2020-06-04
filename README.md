## Build Docker Image
`docker build -t gcr.io/PROJECT_ID/hello-kubernetes:v1 .`

## Run Docker container
`docker run -d -p 8080:8080 gcr.io/PROJECT_ID/hello-kubernetes:v1`

## Push Docker Image Into Google Container Registry
`docker push gcr.io/PROJECT_ID/hello-kubernetes:v1`

## Configure GCP Project ID
`gcloud config set project PROJECT_ID`

## Configure GCP Zone
`gcloud config set compute/zone us-central1-a`

## Create Kubernetes Engine cluster
`gcloud container clusters create hello-kubernetes --num-nodes 2 --machine-type n1-standard-1`

## Create Kubernetes Pod
`kubectl run hello-kubernetes --image=gcr.io/PROJECT_ID/hello-kubernetes:v1 --port=8080`

## Show Services Information
`kubectl get services`

Will show all services information including extenral IP address for the exposed services

## Allow external traffic

By default, the pod is only accessible by its internal IP within the cluster. In order to make the hello-kubernetes container accessible from outside the Kubernetes virtual network, you have to expose the pod as a Kubernetes service.

`kubectl expose deployment hello-kubernetes --type="LoadBalancer" --port=8080`

## Scale up
`kubectl scale deployment hello-kubernetes --replicas=4`

### Orchestrating the Cloud with Kubernetes
https://codelabs.developers.google.com/codelabs/cloud-orchestrate-with-kubernetes/#0
