git clone https://github.com/nigelpoulton/TheK8sBook.git

kubectl create configmap testmap1 \
--from-literal shortname=AOS \
--from-literal longname="Agents of Shield"

kubectl describe cm testmap1

kubectl get cm

kubectl describe cm testmap2

kubectl get cm testmap1 -o yaml

kubectl apply -f multimap.yml

kubectl apply -f singlemap.yml

kubectl describe cm test-config

kubectl apply -f envpod.yml

kubectl exec envpod -- env | grep NAME

kubectl apply -f startuppod.yml

kubectl logs startup-pod -c args1

kubectl describe pod startup-pod

kubectl apply -f cmpod.yml

kubectl exec cmvol -- ls /etc/name

kubectl edit cm multimap

kubectl exec cmvol -- ls /etc/name

kubectl exec cmvol -- cat /etc/name/Country



kubectl create secret generic creds --from-literal user=nigelpoulton \
--from-literal pwd=Password123

kubectl get secret creds -o yaml

echo UGFzc3dvcmQxMjM= | base64 -d

kubectl apply -f secretpod.yml

kubectl exec secret-pod -- ls /etc/tkb

kubectl exec secret-pod -- cat /etc/tkb/password

kubectl get pods

kubectl delete pods --all

kubectl get cm

kubectl delete cm --all

kubectl get secrets

kubectl delete secret --all