kubectl create configmap my-config \
--from-file=my-config.txt \
--from-literal=extra-param=extra-value \
--from-literal=another-param=another-value

kubectl get configmaps my-config -o yaml

curl -o kuard.crt https://storage.googleapis.com/kuar-demo/kuard.crt
curl -o kuard.key https://storage.googleapis.com/kuar-demo/kuard.key

kubectl create secret generic kuard-tls \
--from-file=kuard.crt \
--from-file=kuard.key

kubectl describe secrets kuard-tls

kubectl get secrets

kubectl get configmaps

kubectl describe configmap my-config


kubectl create secret
kubectl create configmap

--from-file=<filename>
Load from the file with the secret data key the same as the filename.
--from-file=<key>=<filename>
Load from the file with the secret data key explicitly specified.
--from-file=<directory>
Load all the files in the specified directory where the filename is an acceptable
key name.
--from-literal=<key>=<value>
Use the specified key/value pair directly.

kubectl replace -f <filename> # for a new version replacing older version or

kubectl apply -f <filename> # for a new version replacing older version or creating if it does not exist

kubectl create secret generic kuard-tls \
--from-file=kuard.crt --from-file=kuard.key \
--dry-run -o yaml | kubectl replace -f -

kubectl edit configmap my-config

kubectl delete configmap my-config

kubectl delete secret kuard-tls