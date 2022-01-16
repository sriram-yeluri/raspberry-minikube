# raspberry-minikube
Minikube on raspberry pi

https://minikube.sigs.k8s.io/docs/start/

```sh
# Download minikubr for arm64 and install the package
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_arm64.deb
sudo dpkg -i minikube_latest_arm64.deb
```

### Minikube Installation and Startup

```sh
sriram@ubuntu:~/Downloads$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_arm64.deb
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 20.3M  100 20.3M    0     0  2597k      0  0:00:08  0:00:08 --:--:-- 2929k
sriram@ubuntu:~/Downloads$ ls
minikube_latest_arm64.deb  vsts-agent-linux-arm64-2.193.0.tar.gz
sriram@ubuntu:~/Downloads$ sudo dpkg -i minikube_latest_arm64.deb
[sudo] password for sriram: 
Selecting previously unselected package minikube.
(Reading database ... 174639 files and directories currently installed.)
Preparing to unpack minikube_latest_arm64.deb ...
Unpacking minikube (1.24.0-0) ...
Setting up minikube (1.24.0-0) ...
sriram@ubuntu:~/Downloads$ minikube status
🤷  Profile "minikube" not found. Run "minikube profile list" to view all profiles.
👉  To start a cluster, run: "minikube start"
sriram@ubuntu:~/Downloads$ minikube start
😄  minikube v1.24.0 on Ubuntu 21.10 (arm64)
✨  Automatically selected the docker driver. Other choices: ssh, none
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
    > gcr.io/k8s-minikube/kicbase: 321.58 MiB / 321.58 MiB  100.00% 1.31 MiB p/
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
    > kubectl.sha256: 64 B / 64 B [--------------------------] 100.00% ? p/s 0s
    > kubelet.sha256: 64 B / 64 B [--------------------------] 100.00% ? p/s 0s
    > kubeadm.sha256: 64 B / 64 B [--------------------------] 100.00% ? p/s 0s
    > kubeadm: 40.50 MiB / 40.50 MiB [-------------] 100.00% 925.08 KiB p/s 45s
    > kubectl: 41.44 MiB / 41.44 MiB [-------------] 100.00% 913.69 KiB p/s 47s
    > kubelet: 107.26 MiB / 107.26 MiB [------------] 100.00% 1.68 MiB p/s 1m4s

    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: default-storageclass, storage-provisioner
💡  kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
sriram@ubuntu:~/Downloads$
```

