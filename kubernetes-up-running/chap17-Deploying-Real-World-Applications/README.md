kubectl create namespace jupyter

kubectl create -f jupyter.yaml

kubectl get pods --namespace jupyter --watch

pod_name=$(kubectl get pods --namespace jupyter --no-headers | awk '{print $1}') \
kubectl logs --namespace jupyter ${pod_name}

echo ${pod-name}

kubectl port-forward ${pod_name} 8888:8888

kubectl get pods --namespace jupyter --no-headers | awk '{print $1}' | head -n 1 | xargs kubectl logs --namespace jupyter

# Clean up

kubectl delete -f jupyter.yaml

kubectl delete namespace jupyter



git clone https://github.com/ParsePlatform/parse-server

cd parse-server

docker build -t ${DOCKER_USER}/parse-server .

docker push ${DOCKER_USER}/parse-server

kubectl create -f parse.yaml

kubectl create -f parse-service.yaml

# Clean up

kubectl delete -f parse.yaml
kubectl delete -f parse-service.yaml



kubectl create cm --from-file ghost-config.js ghost-config

kubectl apply -f ghost.yaml

kubectl expose deployments ghost --port=2368

kubectl proxy

kubectl create configmap ghost-config-mysql --from-file ghost-config.js

kubectl exec -it mysql-zzmlw -- mysql -u root -p

kubectl apply -f ghost.yaml

# Clean up
kubectl delete -f ghost.yaml
kubectl delete configmap ghost-config-mysql
kubectl delete svc ghost
kubectl delete configmap ghost-config






kubectl create configmap \
--from-file=slave.conf=./slave.conf \
--from-file=master.conf=./master.conf \
--from-file=sentinel.conf=./sentinel.conf \
--from-file=init.sh=./init.sh \
--from-file=sentinel.sh=./sentinel.sh \
redis-config

kubectl apply -f redis.yaml

kubectl exec redis-2 -c redis \
-- redis-cli -p 26379 sentinel get-master-addr-by-name redis

kubectl exec redis-2 -c redis -- redis-cli -p 6379 get foo

kubectl exec redis-2 -c redis -- redis-cli -p 6379 set foo 10

kubectl exec redis-0 -c redis -- redis-cli -p 6379 set foo 10

kubectl exec redis-2 -c redis -- redis-cli -p 6379 get foo

# Clean up
kubectl delete cm redis-config
kubectl delete -f redis.yaml