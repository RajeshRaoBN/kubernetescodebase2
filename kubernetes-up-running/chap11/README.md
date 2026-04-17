kind create cluster

kind create cluster --name my-dev-cluster

docker ps

kubectl get nodes

kind get clusters

kubectl apply -f fluentd.yaml -n fluentd

kubectl get namespaces

kubectl create namespaces fluentd

kubectl describe daemonset fluentd -n fluentd

kubectl get pods -o wide -n fluentd

kubectl label nodes <k8 node name> ssd=true

kubectl get nodes --show-labels

kubectl get nodes --selector ssd=true

kubectl apply -f nginx-fast-storage.yaml -n fluentd

kubectl get pods -o wide -n fluentd

kubectl delete -f fluentd.yaml -n fluentd

kubectl delete -f nginx-fast-storage.yaml -n fluentd
