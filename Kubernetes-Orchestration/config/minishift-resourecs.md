https://www.okd.io/minishift/

https://github.com/minishift/minishift/releases

https://docs.okd.io/latest/minishift/getting-started/setting-up-virtualization-environment.html


https://docs.okd.io/latest/minishift/getting-started/quickstart.html

https://docs.okd.io/latest/minishift/getting-started/index.html

https://github.com/dhiltgen/docker-machine-kvm#quick-start-instructions

https://opensource.com/article/18/11/local-okd-cluster-linux

https://www.okd.io/download.html#oc-platforms

https://github.com/openshift/origin/releases/tag/v3.11.0


************************


https://opensource.com/article/18/11/local-okd-cluster-linux

 On Ubuntu 16
  sudo apt install libvirt-bin qemu-kvm
sudo usermod -a -G libvirtd $(whoami)
  newgrp libvirtd

  

For Ubuntu-16.04 and higher

# sudo curl -L https://github.com/dhiltgen/docker-machine-kvm/releases/download/v0.10.0/docker-machine-driver-kvm-ubuntu16.04 -o /usr/local/bin/docker-machine-driver-kvm
# sudo chmod +x /usr/local/bin/docker-machine-driver-kvm

////****************

https://docs.okd.io/latest/minishift/getting-started/quickstart.html#starting-minishift

 To start with kvm driver

  minishift delete --force --clear-cache

  sudo minishift start

  sudo  minishift start --show-libmachine-logs -v5

  sudo  minishift status

  sudo minishift delete --force --clear-cache

minishift status

//////****

Setting Up Minishift to Use VirtualBox

VirtualBox must be manually installed in order to use the embedded VirtualBox drivers. VirtualBox version 5.1.12 or later is required. Ensure that you download and install VirtualBox before using the embedded drivers.

VirtualBox must be identified to Minishift through either the --vm-driver virtualbox flag or persistant configuration options.
Use VirtualBox Temporarily

The --vm-driver virtualbox flag will need to be given on the command line each time the minishift start command is run. For example:

$ minishift start --vm-driver virtualbox

Use VirtualBox Permanently

Setting the vm-driver option as a persistent configuration option allows you to run minishift start without explicitly passing the --vm-driver virtualbox flag each time. You may set the vm-driver persistent configuration option as follows:

$ minishift config set vm-driver virtualbox

The vm-driver persistent configuration option must be supplied before minishift start has been run. If you have already run minishift start, ensure that you run minishift delete, set the configuration with minishift config set vm-driver virtualbox, then run minishift start in order to make use of the VirtualBox driver.
******************//
  To set the path of minishift binary

    Open the .bashrc file in your home directory (for example, /home/your-user-name/.bashrc ) in a text editor.
    Add export PATH="your-dir:$PATH" to the last line of the file, where your-dir is the directory you want to add.
    Save the .bashrc file.
    Restart your terminal.

/home/dell/Desktop/MiniShift/minishift-1.34.1-linux-amd64

 

export PATH="/home/dell/Desktop/MiniShift/minishift-1.34.1-linux-amd64:$PATH"

 
  minishift start --show-libmachine-logs -v5

  sudo ./minishift start --show-libmachine-logs -v5 --iso-url file:////home/dell/Downloads/minishift-centos7.iso

https://github.com/minishift/minishift-centos-iso/releases/download/v1.15.0/minishift-centos7.iso

/home/dell/Downloads

  *****************************************
  https://docs.okd.io/latest/minishift/getting-started/quickstart.html#starting-minishift

  minishift start

