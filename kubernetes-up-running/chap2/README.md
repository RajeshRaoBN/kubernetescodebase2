npm init -y

# edit package.json

npm i -D nodemon

npm i express

npm run dev # Test if everything is working



docker build -t simple-node .

docker run --rm -p 3000:3000 simple-node



docker build -t kuard .
docker run --rm -p 8080:8080 kuard

docker tag kuard gcr.io/kuar-demo/kuard-amd64:blue

docker push gcr.io/kuar-demo/kuard-amd64:blue

docker run -d --name kuard \
 --publish 8080:8080 \
 gcr.io/kuar-demo/kuard-amd64:blue

docker stop kuard
docker rm kuard

dockerr run -d --name kuard \
 --publish 8080:8080 \
 --memory 200m \
 --memory-swap 1G \
 gcr.io/kuar-demo/kuard-amd64:blue

docker run -d --name kuard \
 --publish 8080:8080 \
 --memory 200m \
 --memory-swap 1G \
 --cpu-shares 1024 \
 gcr.io/kuar-demo/kuard-amd64:blue

docker rmi <tag-name>
docker rmi <image-id>