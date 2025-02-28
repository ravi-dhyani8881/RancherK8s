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
