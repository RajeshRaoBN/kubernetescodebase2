kubectl api-resources --sort-by name -o wide

kubectl config view

kubectl config view --raw -o json \
| jq ".users[] | select(.name==\"docker-desktop\")" \
| jq -r '.user["client-certificate-data"]' \
| base64 -d | openssl x509 -text | grep "Subject:"

kubectl describe clusterrole cluster-admin

kubectl describe clusterrolebindings cluster-admin

kubectl describe pod kube-apiserver-docker-desktop \
--namespace kube-system | grep admission