kind create cluster --wait 5m \
export KUBECONFIG="$(kind get kubeconfig-path)"
kubectl cluster-info

kubectl get componentstatuses

kubectl get nodes

kubectl describe nodes node-1

kubectl describe nodes node-1 > describe.yaml

kubectl get namespace

kubectl get daemonSets --namespace=kube-system kube-proxy

kubectl get deployments --namespace=kube-system core-dns

kubectl get services --namespace=kube-system core-dns

kubectl get deployments --namespace=kube-system kubernetes-dashboard

kubectl get services --namespace=kube-system kubernetes-dashboard

kubectl proxy

kind delete cluster