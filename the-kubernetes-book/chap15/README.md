kubectl cluster-info

kubectl get pods --namespace shield

kubectl proxy --port 9000 &

curl -X GET http://localhost:9000/api/v1/namespaces/shield/pods

curl -X GET http://localhost:9000/api/v1/namespaces

curl -v -X GET http://localhost:9000/api/v1/namespaces/shield/pods

curl -X POST -H "Content-Type: application/json" \
--data-binary @ns.json http://localhost:9000/api/v1/namespaces

kubectl get namespaces

curl -X DELETE \
-H "Content-Type: application/json" http://localhost:9000/api/v1/namespaces/shield

kubectl api-resources

for kind in `kubectl api-resources | tail +2 | awk '{ print $1 }'`; \
do kubectl explain $kind; done | grep -e "KIND:" -e "VERSION:"

curl http://localhost:9000/api

curl http://localhost:9000/apis

curl http://localhost:9000/api/v1/namespaces

kubectl apply -f deprecate.yml

kubectl apply -f crd.yml

kubectl api-resources | grep books

kubectl explain book

kubectl apply -f kcna.yml

kubectl get bk

kubectl proxy --port 9000 &

curl http://localhost:9000/apis/nigelpoulton.com/v1/

ps | grep kubectl proxy

kill -9 27533

kubectl delete book kcna

kubectl delete crd books.nigelpoulton.com