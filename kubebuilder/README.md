mkdir -p ~/projects/guestbook
cd ~/projects/guestbook
kubebuilder init --domain my.domain --repo my.domain/guestbook

kubebuilder create api --group webapp --version v1 --kind Guestbook

make manifests

kubectl cluster-info

make install

make run

kubectl apply -k config/samples/

kubectl get guestbooks.webapp.my.domain guestbook-sample -o yaml

make docker-build docker-push IMG=<some-registry>/<project-name>:tag

make uninstall

make undeploy
