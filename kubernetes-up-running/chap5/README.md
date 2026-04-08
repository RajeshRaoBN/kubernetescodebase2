kubectl run kuard --image=gcr.io/kuar-demo/kuard-amd64:blue

kubectl get pods

kubectl delete pods/kuard

docker run -d --name kuard \
 --publish 8080:8080 \
 gcr.io/kuar-demo/kuard-amd64:blue

 kubectl apply -f kuard-pod.yaml

 kubectl get pods -o wide/yaml

 kubectl describe pods kuard

 kubectl delete pods/kuard

 kubectl delete -f kuard-pod.yaml

 kubectl port-forward kuard 8080:8080

 kubectl logs kuard -f

 kubectl exec kuard date

 kubectl exec -it kuard ash

 kubectl cp <pod-name>:/captures/capture3.txt ./capture3.txt

 kubectl cp $HOME/config.txt <pod-name>:/config.txt

 kubectl apply -f kuard-pod-health.yaml
 kubectl port-forward kuard 8080:8080