# kubernative-cluster-localhost using minikube or kind
This repository provides a comprehensive guide for setting up a Kubernative cluster on your localhost using either Minikube or Kind (Kubernetes IN Docker).

Method 1: Using Minikube
1) Install Minikube:
Follow the installation instructions for your operating system from the Minikube installation guide.
2) Start Minikube:
Open your terminal and run the following command to start Minikube with a single master node and two worker nodes:
```
minikube start --nodes 3
```
By default, Minikube creates one master node and two worker nodes when you specify --nodes 
3) After Minikube starts, you can verify the nodes by running:
```
kubectl get nodes
```

Method 2: Using kind (Kubernetes in Docker)
Install kind:
You can install kind by following the instructions in the kind installation guide.
Create a Cluster Configuration:
Create a configuration file named kind-config.yaml with the following content:
```
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
networking:
  disableDefaultCNI: false
nodes:
  - role: control-plane
  - role: worker
  - role: worker

```

3) Create the Cluster
   Run the following command to create the cluster using the configuration file
   ```
   kind create cluster --config kind-config.yaml
   ```
4) Verify the Cluster:
   After the cluster is created, you can verify the nodes by running:

   ```
   kubectl get nodes
```
Additional Notes
kubectl: Make sure you have kubectl installed to interact with your Kubernetes cluster. You can install it by following the instructions in the kubectl installation guide.
