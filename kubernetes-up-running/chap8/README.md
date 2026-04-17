minikube start

minikube addons enable ingress

kubectl get pods -n ingress-nginx

# create example folder with three files

kubectl apply -f example

minikube tunnel


curl --resolve "www.example.com:80:127.0.0.1" -i http://www.example.com

kubectl exec -n ingress-nginx ingress-nginx-controller-596f8778bc-htvmh -- cat /etc/nginx/nginx.conf



kubectl apply -f https://j.hept.io/contour-deployment-rbac

kubectl get -n projectcontour service contour -o wide

kubectl apply -f ./example/4-simple-ingress.yaml

kubectl get ingress

kubectl describe ingress nginx