# devops-task


# kubeadm setup 

1. created  kubeadm cluster using vagrant 

vagrant up #command will get created one master and 2 worker node 

here we create one init.sh file in this file all containerd and kubeadm related command.

2.  Initialize the cluster, also by passing a flag that is later needed for the networking plugin (CNI).

sudo kubeadm init --apiserver-advertise-address=192.168.56.10  --pod-network-cidr=10.244.0.0/16

3. Install the Calico Networking Plugin in the Cluster (This will handle networking between different pods and nodes)


kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml


4. The kubeadm init command that you ran previously on the master should output a kubeadm join command containing a token and hash. If you have copied that command from the master and saved it somewhere, run it on both worker nodes with sudo to connect them to the master.

5. helm chat step 

Get values file from

https://github.com/kubernetes/ingress-nginx/tree/master/charts/ingress-nginx


Initialize a Helm Chart Repository


helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

Install Nginx Ingress Helm Chart 

helm install sample-ingress ingress-nginx/ingress-nginx -f values.yaml


Deploy Sample App

kubectl apply -f sample-app.yaml







