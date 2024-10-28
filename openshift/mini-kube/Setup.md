This setpup is specific for the Redhat Linux version 9.4

1. Install podman

   ```
   > sudo dnf install -y podman
   ```
2. Verify the version

   ```
   > podman version 
   Client:       Podman Engine
   Version:      4.9.4-rhel
   API Version:  4.9.4-rhel
   Go Version:   go1.21.13 (Red Hat 1.21.13-4.el9_4)
   Built:        Fri Oct 11 11:02:32 2024
   OS/Arch:      linux/amd64

   ```
3. Allow your local user to run podman commands with sudo

   ```
   > echo "<user-name> ALL=(ALL) NOPASSWD: /usr/bin/podman" | sudo tee /etc/sudoers.d/<user-name>

   ```
4. Install kubectl command line client

   ```
   > curl -LO https://storage.googleapis.com/kubernetes-release/release/\
   `curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
   ```
5. Verify the binary

   ```
   > curl -LO "https://dl.k8s.io/release/$(curl -L -s 
   https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
   > echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
   kubectl: OK
   ```
6. ```
   sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
   ```
7. Download stable version of MiniKube and install using rpm package manager.

   ```
   > curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
   > sudo rpm -Uvh minikube-latest.x86_64.rpm
   ```
8. Start the cluster

   ```
   > minikube start
   😄  minikube v1.34.0 on Redhat 9.4
   ✨  Using the podman driver based on user configuration
   📌  Using Podman driver with root privileges
   👍  Starting "minikube" primary control-plane node in "minikube" cluster
   🚜  Pulling base image v0.0.45 ...
   💾  Downloading Kubernetes v1.31.0 preload ...
       > gcr.io/k8s-minikube/kicbase...:  487.89 MiB / 487.90 MiB  100.00% 3.23 Mi
       > preloaded-images-k8s-v18-v1...:  326.69 MiB / 326.69 MiB  100.00% 2.08 Mi
   E1028 18:00:12.395166   24770 cache.go:189] Error downloading kic artifacts:  not yet implemented, see issue #8426
   🔥  Creating podman container (CPUs=2, Memory=7800MB) ...
   🐳  Preparing Kubernetes v1.31.0 on Docker 27.2.0 ...
       ▪ Generating certificates and keys ...
       ▪ Booting up control plane ...
       ▪ Configuring RBAC rules ...
   🔗  Configuring bridge CNI (Container Networking Interface) ...
   🔎  Verifying Kubernetes components...
       ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
   🌟  Enabled addons: storage-provisioner, default-storageclass
   🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
   ```
9. In newer verion of mini-kube, essential addons are  available by default and dashboard is one of them. Retrieve the dashboad and view the resourses in the cluster.

   ```
   > minikube dashboar d--url
   🔌  Enabling dashboard ...
       ▪ Using image docker.io/kubernetesui/metrics-scraper:v1.0.8
       ▪ Using image docker.io/kubernetesui/dashboard:v2.7.0
   💡  Some dashboard features require the metrics-server addon. To enable all features please run:

   	minikube addons enable metrics-server

   🤔  Verifying dashboard health ...
   🚀  Launching proxy ...
   🤔  Verifying proxy health ...
   http://127.0.0.1:45745/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/

   ```
10. Test cluster with a sample deployment

    ```
    > kubectl create deployment nginx-test --image=nginx --replicas=2
    > kubectl expose deployment nginx-test --type NodePort --port=80
    > kubectl get pods
    > kubectl get deployment nginx-test

    ```
