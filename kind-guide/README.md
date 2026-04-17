brew install kind

kind create cluster --name kind-cluster

kind get clusters

kubectl cluster-info --context kind-kind

kind delete cluster




kind load docker-image my-app:latest

kind load docker-image my-app:latest my-db:latest my-cache:latest
