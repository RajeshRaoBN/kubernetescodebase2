docker run busybox echo "Hello world"

docker run ubuntu echo "Hello world"

docker run --rm fedora echo "Hello world"

# using a public image from docker hub

docker run --rm -v $(pwd):/app -w /app dhi.io/dart:3 sh -c 'cat > hello.dart << EOF
void main() {
  print("Hello from DHI Dart!");
}
EOF
dart run hello.dart'

docker build -t kubia .

docker images

docker run --name kubia-container -p 8080:8080 -d kubia

curl localhost:8080

docker ps

docker inspect kubia-container

docker exec -it kubia-container bash
docker exec -it kubia-container sh
    ps aux
    ps aux | grep app.js
    ls /
    exit

docker stop kubia-container

docker rm kubia-container

docker tag kubia rbnrao/kubia

docker images | head

docker push rbnrao/kubia
# if needed do a % docker login

docker run -p 8080:8080 -d rbnrao/kubia







kubectl cluster-info

kubectl apply -f kubia.yaml

kubectl get pods

kubectl describe pod kubia-xxxx

kubectl get nodes

kubectl describe node node-name

kubectl run kubia --image=rbnrao/kubia --port=8080

kubectl get pods

kubectl expose pod kubia --type=LoadBalancer --name=kubia-http --port=8080

kubectl port-forward svc/kubia-http 8080:8080

kubectl get services

localhost:8080

kubectl get replicationcontrollers

kubectl get pods

curl localhost:8080

kubectl get pods -o wide

kubectl describe pod kubia

kubectl cluster-info | grep dashboard

kind get clusters

# Add kubernetes-dashboard repository
helm repo add kubernetes-dashboard https://kubernetes.github.io/dashboard/
# Deploy a Helm Release named "kubernetes-dashboard" using the kubernetes-dashboard chart
helm upgrade --install kubernetes-dashboard kubernetes-dashboard/kubernetes-dashboard --create-namespace --namespace kubernetes-dashboard

kubectl -n kubernetes-dashboard port-forward svc/kubernetes-dashboard-kong-proxy 8443:443

kubectl delete -f kubia.yaml

kubectl delete svc kubia-http

kubectl delete pod kubia