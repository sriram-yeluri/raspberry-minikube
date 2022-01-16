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

### pods status running in the cluster 

```sh
sriram@ubuntu:~/Downloads$ minikube kubectl -- get po -A
NAMESPACE     NAME                               READY   STATUS    RESTARTS      AGE
kube-system   coredns-78fcd69978-sswhq           1/1     Running   0             14m
kube-system   etcd-minikube                      1/1     Running   0             14m
kube-system   kube-apiserver-minikube            1/1     Running   0             14m
kube-system   kube-controller-manager-minikube   1/1     Running   0             14m
kube-system   kube-proxy-wsszj                   1/1     Running   0             14m
kube-system   kube-scheduler-minikube            1/1     Running   0             14m
kube-system   storage-provisioner                1/1     Running   1 (13m ago)   14m
```

### Download kubectl for arm64

```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl"
chmod +x kubectl
sudo cp kubectl /usr/bin/
```

### kubectl status

```sh
sriram@ubuntu:~$ kubectl get pods -A
NAMESPACE              NAME                                         READY   STATUS    RESTARTS      AGE
kube-system            coredns-78fcd69978-sswhq                     1/1     Running   0             32m
kube-system            etcd-minikube                                1/1     Running   0             32m
kube-system            kube-apiserver-minikube                      1/1     Running   0             32m
kube-system            kube-controller-manager-minikube             1/1     Running   0             32m
kube-system            kube-proxy-wsszj                             1/1     Running   0             32m
kube-system            kube-scheduler-minikube                      1/1     Running   0             32m
kube-system            storage-provisioner                          1/1     Running   1 (31m ago)   32m
kubernetes-dashboard   dashboard-metrics-scraper-5594458c94-npz5p   1/1     Running   0             16m
kubernetes-dashboard   kubernetes-dashboard-654cf69797-gkd7t        1/1     Running   0             16m

sriram@ubuntu:~$ kubectl get nodes
NAME       STATUS   ROLES                  AGE   VERSION
minikube   Ready    control-plane,master   32m   v1.22.3
```
