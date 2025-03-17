# RancherK8s
RancherK8s
# Install RAncher and k8s cluster
K8s set up in Codespace

https://github.com/codespaces-lab/kubernetes-in-codespaces

Install Rancher on top link [
](https://ranchermanager.docs.rancher.com/getting-started/installation-and-upgrade/other-installation-methods/rancher-on-a-single-node-with-docker
)

docker run -d --restart=unless-stopped \
  -p 80:80 -p 443:443 \
  --privileged \
  rancher/rancher:latest
  
If Rancher not run after restart codespace 
sudo dockerd --host=unix:///var/run/docker.sock --host=tcp://0.0.0.0:2375 &


1) Download the kubeconfig file 

2) Then run bellow command 

kubectl config view --raw -o jsonpath='{.clusters[0].cluster.certificate-authority-data}' | base64 --decode > ca.crt

3) Then inside the config file provide path like this 


apiVersion: v1
kind: Config
clusters:
- name: "local"
  cluster:
    server: "https://fictional-doodle-w9qgrgvv9729j9p-443.app.github.dev/k8s/clusters/local"
    certificate-authority: "/Users/ravi.dhyani/test/ca.crt"

users:
- name: "local"
  user:
    token: "kubeconfig-user-bmz6t8svr4:5zzzlf52ttz22qx7zgbh2f59x8gbdxqhqntm469tpr5x6sd64knzrh"


contexts:
- name: "local"
  context:
    user: "local"
    cluster: "local"

current-context: "local"

Step 4) Then run the bellow command 

 kubectl config set-cluster local --insecure-skip-tls-verify=true

Step 5) Then use kubectl get ns



