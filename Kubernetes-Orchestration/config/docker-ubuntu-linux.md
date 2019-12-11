  Docker 18.03 for Ubuntu Linux

  https://docs.docker.com/install/linux/docker-ce/ubuntu/

  Install Docker CE version 18.06.2   for Kubernetes kubeadm ver 1.16

  https://kubernetes.io/docs/setup/production-environment/container-runtimes/

  Uninstall perv versions

  sudo apt-get remove docker docker-engine docker.io containerd runc

 sudo apt-get remove docker-ce docker-ce-cli containerd.io

   
  Install a specific version using the version  string
  
 sudo su

 apt-get update && apt-get install apt-transport-https ca-certificates curl software-properties-common


  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -


  ## Install Docker CE ver 18.06.2

apt-get update && apt-get install docker-ce=18.06.2~ce~3-0~ubuntu

  # Setup daemon.
cat > /etc/docker/daemon.json <<EOF
{
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2"
}
EOF

  Verifyu
  cat  /etc/docker/daemon.json
  mkdir -p /etc/systemd/system/docker.service.d


   #Restart docker.
   systemctl daemon-reload
   systemctl restart docker

   
    su>exit
    
 docker info
 docker version



 




