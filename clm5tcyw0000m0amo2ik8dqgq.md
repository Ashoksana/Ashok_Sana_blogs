---
title: "Setting Up Kubernetes on Ubuntu"
datePublished: Tue Sep 05 2023 04:31:42 GMT+0000 (Coordinated Universal Time)
cuid: clm5tcyw0000m0amo2ik8dqgq
slug: setting-up-kubernetes-on-ubuntu
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693888068531/6cfbbb6b-7229-4ddb-9577-17e901b73113.png
tags: ubuntu, docker, kubernetes, devops, 90daysofdevops

---

To set up Kubernetes on an Ubuntu instance (t2.medium) with the provided security groups, follow these detailed steps:

1. **Launch Ubuntu Instance (t2.medium)**
    
    * Launch an Ubuntu instance with the specified security groups (80, 8080, 443, 6783, 6784, 6443).
        
2. **Update Packages and Install Dependencies**
    
    ```bash
    sudo su
    sudo apt-get update -y
    sudo apt-get install -y apt-transport-https
    sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
    ```
    
3. **Configure Kubernetes Repository**
    
    ```bash
    vi /etc/apt/sources.list.d/kubernetes.list
    ```
    
    Add this line to the file:
    
    ```bash
    deb http://apt.kubernetes.io/ kubernetes-xenial main
    ```
    
    Save and exit.
    
4. **Install Docker**
    
    ```bash
    apt-get update -y
    apt-get install docker.io -y
    systemctl enable docker
    systemctl start docker
    usermod -a -G docker ubuntu
    ```
    
5. **Install Kubernetes Components**
    
    ```bash
    apt-get install -y kubelet kubeadm kubectl kubernetes-cni
    ```
    
    If there's an error with Kubernetes CNI, run:
    
    ```bash
    sudo dpkg -i --force-overwrite /var/cache/apt/archives/kubernetes-cni_0.7.5-00_amd64.deb
    ```
    
6. **Configure cgroup Driver for Kubelet**
    
    ```bash
    vi /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
    ```
    
    Add this line:
    
    ```bash
    makefileCopy codeEnvironment="cgroup-driver=systemd/cgroup-driver=cgroupfs"
    ```
    
    Save and exit.
    
7. **Create an AMI (e.g., devops-k8s)**
    
8. **Initialize Kubernetes Cluster**
    
    ```bash
    kubeadm init
    kubectl get nodes  # This might show an error for now
    ```
    
    Exit from the root user.
    
9. **Configure kubectl**
    
    ```bash
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    kubectl get nodes  # This should display your nodes
    ```
    
10. **Enable IP Forwarding**
    
    ```bash
    sudo su
    sysctl net.bridge.bridge-nf-call-iptables=1
    exit
    ```
    
11. **Set Up Networking (Weave)**
    
    ```bash
    export kubever=$(kubectl version | base64 | tr -d '\n')
    kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$kubever"
    kubectl get pods --all-namespaces
    kubectl get nodes
    ```
    
12. **Launch Instances with the Created AMI**
    
    * Launch instances with the specified security groups (80, 8080, 8081, 8083).
        
13. **Join Worker Nodes to the Cluster**
    
    * SSH into each worker node and run the join command obtained from the master node. Example:
        
    
    ```bash
    kubeadm join 172.31.38.233:6443 --token oiqur0.u6actvi9k6bc5oex \
        --discovery-token-ca-cert-hash sha256:a869eb97f1f6f2759a39645f5976130aeddb2604fc45bb1e949e67e04f3fc3f5
    ```
    
    To generate a new token, use `kubeadm token create --print-join-command`.
    
14. **Access Kubernetes Dashboard**
    
    * To install the Kubernetes dashboard, use:
        
    
    ```bash
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
    ```
    
    * Create a service account and cluster role binding:
        
    
    ```bash
    vi service.yaml
    ```
    
    Add:
    
    ```yaml
    apiVersion: v1
    kind: ServiceAccount
    metadata:
      name: admin-user
      namespace: kube-system
    ```
    
    Save and exit.
    
    ```bash
    kubectl apply -f service.yaml
    ```
    
    ```bash
    vi role.yaml
    ```
    
    Add:
    
    ```yaml
    apiVersion: rbac.authorization.k8s.io/v1
    kind: ClusterRoleBinding
    metadata:
      name: admin-user
    roleRef:
      apiGroup: rbac.authorization.k8s.io
      kind: ClusterRole
      name: cluster-admin
    subjects:
    - kind: ServiceAccount
      name: admin-user
      namespace: kube-system
    ```
    
    Save and exit.
    
    ```bash
    kubectl apply -f role.yaml
    ```
    
    * Get the dashboard token:
        
    
    ```bash
    kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print  $1}')
    ```
    
    * Start the proxy:
        
    
    ```bash
    nohup kubectl proxy --address 0.0.0.0 --accept-hosts '.*' &
    ```
    
    * Find the Kubernetes dashboard ClusterIP:
        
    
    ```bash
    kubectl -n kube-system get service kubernetes-dashboard
    ```
    
    Edit the service to use NodePort instead of ClusterIP:
    
    ```bash
    kubectl -n kube-system edit service kubernetes-dashboard
    ```
    
    Change `Type: ClusterIP` to `Type: NodePort`.
    
    * Access the dashboard via a web browser at [`https://ip:30293`](https://ip:30293) and provide the dashboard token when prompted.
        
15. **Deploy and Manage Applications**
    
    * You can deploy and manage applications using `kubectl`. For example:
        
    
    ```bash
    kubectl run testk8s --image=nginx
    kubectl get pods
    kubectl run test1k8s --image=nginx
    kubectl delete pod testk8s
    ```
    
16. **Understanding Kubernetes Resources**
    
    * Kubernetes has several resources, including Pods, ReplicaSets, and Deployments, to manage your applications.
        
    * To create a Pod:
        
    
    ```bash
    kubectl run kuard --generator=run-pod/v1 --image gcr.io/kuar-demo/kuard-amd64:1
    ```
    
    * To find a Pod's IP address:
        
    
    ```bash
    kubectl get pods -o wide
    ```
    
    * To forward ports to a Pod:
        
    
    ```bash
    kubectl port-forward kuard 8080:8080
    ```
    
    * To delete a Pod:
        
    
    ```bash
    kubectl delete pod kuard
    ```
    
    * Explore more about Pods, ReplicaSets, and Deployments in [**Kubernetes Basics**](https://kubernetes.io/docs/tutorials/kubernetes-basics/create-cluster/cluster-intro/).
        

1. Hope you like my blog...!
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692351695778/c9653064-2cfb-48eb-9cf3-9fcc3a16bfe7.png align="center")
    
    If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)
    
    Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)
    
    [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)
    
    Happy learning......!