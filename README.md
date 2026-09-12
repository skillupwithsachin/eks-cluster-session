Namespace
   │
   ├── Pod
   │
   ├── ReplicaSet
   │      │
   │      └── Pods
   │
   ├── Deployment
   │      │
   │      └── ReplicaSet
   │             │
   │             └── Pods
   │
   ├── DaemonSet
   │      └── Pod on each node
   │
   ├── StatefulSet
   │      ├── Pod
   │      └── PVC
   │
   ├── Job
   │
   └── CronJob

Networking
   ├── ClusterIP
   ├── NodePort
   ├── LoadBalancer
   └── Ingress

Configuration
   ├── ConfigMap
   └── Secret

Storage
   ├── StorageClass
   ├── PVC
   └── PV

Security
   ├── ServiceAccount
   ├── Role
   ├── RoleBinding
   ├── ClusterRole
   └── ClusterRoleBinding

Scaling
   ├── HPA
   └── PDB

Scheduling
   ├── Labels
   ├── NodeSelector
   ├── Affinity
   ├── Taints/Tolerations
   └── PriorityClass

Advanced
   ├── NetworkPolicy
   ├── InitContainer
   ├── Sidecar
   ├── Probes
   └── Lifecycle


##How to connect to  EKS cluster
aws eks update-kubeconfig \
  --region us-east-1 \
  --name <cluster-name>

Verify the cluster set-up using:

kubectl config current-context
kubectl get nodes
kubectl get nodes -o wide
kubectl cluster-info 
kubectl api-resources #list all the apis

##how to create namespace
1.To create it via command line using kubectl use below command 
   kubectl create ns <your-namespace-name>
2.To create via the yaml file,use namespace.yaml and run below command
   kubectl apply -f namespace.yaml 


##How to create a pod
1.We can create a pod using kubectl pod command but not recommended
2.The ideal way to create a pod is using pod manifest that is pod.yaml using command
    kubectl apply -f pod.yaml -n <your-namespace-name>
    kubectl get pods -n k8s-demo
    kubectl get pods -o wide -n k8s-demo
    kubectl describe pod nginx-pod -n k8s-demo
    kubectl logs nginx-pod -n k8s-demo
    kubectl exec -it nginx-pod -n k8s-demo -- /bin/bash 
    kubectl delete pod nginx-pod -n k8s-demo


##commands for replicaset.yaml
    kubectl get rs -n k8s-demo
    kubectl get pods -n k8s-demo 