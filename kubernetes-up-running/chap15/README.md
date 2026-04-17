kubectl apply -f nfs-volume.yaml

kubectl apply -f nfs-volume-claim.yaml

kubectl apply -f mysql-replicaset.yaml

kubectl apply -f mysql-service.yaml

kubectl apply -f storageclass.yaml 

kubectl apply -f dynamic-volume-claim.yaml



kubectl apply -f mongo-simple.yaml

kubectl get pods

kubectl apply -f mongo-service.yaml

kubectl run -it --rm --image busybox busybox ping mongo-1.mongo

kubectl exec -it mongo-0 -- mongo
    rs.initiate( {
    _id: "rs0",
    members:[ { _id: 0, host: "mongo-0.mongo:27017" } ]
    });
    OK

    rs.add("mongo-1.mongo:27017");
    rs.add("mongo-2.mongo:27017");

kubectl apply -f mongo-configmap.yaml
kubectl apply -f mongo-service.yaml
kubectl apply -f mongo.yaml