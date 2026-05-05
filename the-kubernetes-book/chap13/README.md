kubectl apply -f gcp-sc.yml/dd-sc.yml

kubectl get sc

kubectl apply -f headless-svc.yml

kubectl get svc

kubectl apply -f sts.yml

kubectl get sts --watch

kubectl get pvc

kubectl apply -f jump-pod.yml

kubectl exec -it jump-pod -- bash

kubectl apply -f sts.yml

kubectl get sts tkb-sts

kubectl get pods

kubectl get pvc

kubectl apply -f sts.yml

kubectl get sts tkb-sts

kubectl describe pod tkb-sts-2 | grep ClaimName

kubectl get pods

kubectl get pods --watch

kubectl describe pod tkb-sts-0 | grep ClaimName

kubectl scale sts tkb-sts --replicas=0

kubectl get sts tkb-sts

kubectl delete sts tkb-sts

kubectl delete pod jump-pod

kubectl delete pvc webroot-tkb-sts-0 webroot-tkb-sts-1 webroot-tkb-sts-2

kubectl delete sc flash