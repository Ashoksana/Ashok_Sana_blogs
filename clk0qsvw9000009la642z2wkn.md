---
title: "Essential Kubernetes Commands Every Developer Should Know"
datePublished: Thu Jul 13 2023 06:01:50 GMT+0000 (Coordinated Universal Time)
cuid: clk0qsvw9000009la642z2wkn
slug: essential-kubernetes-commands-every-developer-should-know
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689227926710/76d66cb3-42f3-450d-ac31-10eb589d14ea.png
tags: kubernetes, devops, kubernetes-container, k8s-commands

---

### **Introduction:**

Kubernetes has become the de facto standard for container orchestration, providing a powerful platform for managing and scaling containerized applications. As a developer working with Kubernetes, it's important to have a solid understanding of the essential kubectl commands to navigate and interact with your clusters effectively. In this blog post, we will explore 25 useful kubectl commands with explanations and examples.

1. **kubectl get pods**:
    
    Description: Lists all running pods in the current namespace.
    
    Example: kubectl get pods.
    
2. **kubectl create deployment --image=**:
    
    Description: Creates a new deployment with the specified name and image. Example: kubectl create deployment nginx-deployment --image=nginx
    
3. **kubectl expose deployment --port=**:
    
    Description: Creates a new service for the specified deployment and exposes it on the specified port.
    
    Example: kubectl expose deployment nginx-deployment --port=80
    
4. **kubectl scale deployment --replicas=**:
    
    Description: Scales the specified deployment to the specified number of replicas.
    
    Example: kubectl scale deployment nginx-deployment --replicas=3
    
5. **kubectl delete deployment :**
    
    Description: Deletes the specified deployment.
    
    Example: kubectl delete deployment nginx-deployment
    
6. **kubectl delete pod :**
    
    Description: Deletes the specified pod.
    
    Example: kubectl delete pod nginx-pod
    
7. **kubectl logs :**
    
    Description: Shows the logs for the specified pod.
    
    Example: kubectl logs nginx-pod
    
8. **kubectl exec -it -- /bin/bash:**
    
    Description: Opens a shell in the specified pod.
    
    Example: kubectl exec -it nginx-pod -- /bin/bash
    
9. **kubectl port-forward** ::
    
    Description: Forwards traffic from the specified local port to the specified remote port on the specified pod.
    
    Example: kubectl port-forward nginx-pod 8080:80
    
10. **kubectl describe :**
    
    Description: Provides detailed information about the specified resource.
    
    Example: kubectl describe pod nginx-pod
    
11. kubectl get nodes:
    
    Description: Lists all the nodes in the cluster.
    
    Example: kubectl get nodes
    
12. **kubectl get services**:
    
    Description: Lists all the services in the current namespace.
    
    Example: kubectl get services
    
13. **kubectl get deployments:**
    
    Description: Lists all the deployments in the current namespace.
    
    Example: kubectl get deployments
    
14. **kubectl get configmaps:**
    
    Description: Lists all the configmaps in the current namespace.
    
    Example: kubectl get configmaps
    
15. **kubectl get secrets:**
    
    Description: Lists all the secrets in the current namespace.
    
    Example: kubectl get secrets
    
16. **kubectl apply -f :**
    
    Description: Applies the configuration file.
    
    Example: kubectl apply -f deployment.yaml
    
17. **kubectl rollout status deployment :**
    
    Description: Shows the status of the specified deployment rollout.
    
    Example: kubectl rollout status deployment nginx-deployment
    
18. **kubectl rollout history deployment :**
    
    Description: Shows the revision history of the specified deployment. Example: kubectl rollout history deployment nginx-deployment
    
19. **kubectl rollout undo deployment :**
    
    Description: Undoes the last rollout of the specified deployment.
    
    Example: kubectl rollout undo deployment nginx-deployment
    
20. **kubectl top :**
    
    Description: Shows the resource usage statistics for the specified resource type.
    
    Example: kubectl top pods
    
21. **kubectl create namespace :**
    
    Description: Creates a new namespace with the specified name.
    
    Example: kubectl create namespace my-namespace
    
22. **kubectl get namespaces:**
    
    Description: Lists all the namespaces in the cluster.
    
    Example: kubectl get namespaces
    
23. **kubectl config get-contexts:**
    
    Description: Lists all the contexts in the Kubernetes configuration file. Example: kubectl config get-contexts
    
24. **kubectl config set-context --namespace=:**
    
    Description: Sets the namespace for the specified context.
    
    Example: kubectl config set-context my-context --namespace=my-namespace
    
25. **kubectl edit :**
    
    Description: Opens the specified resource in the default editor.
    
    Example: kubectl edit deployment nginx-deployment.
    

**Conclusion:**

These 25 kubectl commands are essential for developers working with Kubernetes. By leveraging these commands, you can effectively manage deployments, pods, services, namespaces, and more. Experiment with these commands in your Kubernetes environment and unlock the full potential of this powerful container orchestration platform.

Remember to refer to the official Kubernetes documentation for more detailed explanations and examples of each command. Happy Kubernetes development!

Hope you like my blog...!

if u like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!