auditctl -w /usr/bin/docker -p wxa -k audit-docker           # Auditing files on Linux

kubectl create ns psa-test

kubectl label --overwrite ns psa-test \
pod-security.kubernetes.io/enforce=baseline

kubectl describe ns psa-test

kubectl apply -f psa-pod.yml.          # when security previlages are set to true.

kubectl apply -f psa-pod.yml.          # when security previlages are set to false.

kubectl label --dry-run=server --overwrite ns psa-test \
pod-security.kubernetes.io/enforce=restricted

kubectl label --overwrite ns psa-test \
pod-security.kubernetes.io/enforce=restricted

kubectl get pods --namespace psa-test

kubectl label --overwrite ns psa-test \
pod-security.kubernetes.io/enforce=baseline \
pod-security.kubernetes.io/warn=restricted \
pod-security.kubernetes.io/audit=restricted

# Clean Up
kubectl delete -f psa-pod.yml

kubectl delete ns psa-test