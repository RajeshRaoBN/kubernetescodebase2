kubectl create deployment alpaca-prod --image=gcr.io/kuar-demo/kuard-amd64:blue --replicas=3 --port=8080
kubectl label deployment alpaca-prod ver=1 app=alpaca env=prod --overwrite

kubectl expose deployment alpaca-prod

kubectl create deployment bandicoot-prod --image=gcr.io/kuar-demo/kuard-amd64:green --replicas=2 --port=8080
kubectl label deployment bandicoot-prod ver=2 app=bandicoot env=prod --overwrite

kubectl expose deployment bandicoot-prod

kubectl get services -o wide

ALPACA_POD=$(kubectl get pods -l app=alpaca -o jsonpath='{.items[*].metadata.name}')
# or
ALPACA_POD=$(kubectl get pods -l app=alpaca -o jsonpath='{range .items[*]}{.metadata.name}{"\n"}{end}')

kubectl port-forward $ALPACA_POD 48858:8080

kubectl edit deployment/alpaca-prod

kubectl get endpoints alpaca-prod --watch

kubectl edit service alpaca-prod

ssh <node> -L 8080:localhost:32711

kubectl describe service alpaca-prod

kubectl describe endpoints alpaca-prod

kubectl get endpoints alpaca-prod --watch

kubectl delete deployment alpaca-prod

kubectl create deployment alpaca-prod --image=gcr.io/kuar-demo/kuard-amd64:blue --replicas=3 --port=8080
kubectl label deployment alpaca-prod ver=1 app=alpaca env=prod --overwrite

kubectl get pods -o wide --show-labels

kubectl get pods -o wide --selector=app=alpaca,env=prod

BANDICOOT_POD=$(kubectl get pods -l app=bandicoot \
 -o jsonpath='{.items[0].metadata.name}')

BANDICOOT_POD=$(kubectl get pods -l app=bandicoot -o jsonpath='{.items[*].metadata.name}')
# or
BANDICOOT_POD=$(kubectl get pods -l app=bandicoot -o jsonpath='{range .items[*]}{.metadata.name}{"\n"}{end}')

kubectl port-forward $BANDICOOT_POD 48858:8080

kubectl delete services,deployments -l app