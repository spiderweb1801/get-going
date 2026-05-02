# Kubernetes Basic Commands

This README gives a beginner-friendly overview of Kubernetes nodes, `kubectl`, and a set of common commands used to inspect and manage resources in a cluster. `kubectl` is the Kubernetes command-line tool used to deploy applications, inspect cluster resources, and troubleshoot workloads.[1][2]

## Kubernetes Basics

### Nodes

A Kubernetes cluster is made up of machines called **nodes**, and workloads such as Pods run on worker nodes.[2][3]

- **Worker Node**: Runs application workloads, including containers packaged inside Pods. A production cluster usually has multiple worker nodes for better scalability and availability.[2][3]
- **Master / Control Plane**: Manages the cluster, monitors the overall state, schedules workloads, and coordinates cluster operations.[2]

### Kubectl

`kubectl` is the primary CLI used to deploy and manage applications in a Kubernetes cluster. It is also used to check the status of Pods, inspect resources, and apply configuration files.[1][2]

## Alias

Create a short alias for `kubectl`:

```bash
alias k=kubectl
```

> Note: the correct alias syntax is `alias k=kubectl`, not `alias kubectl k`.[2]

## Basic Commands

### 1. Get cluster nodes

```bash
k get nodes
```

Lists all nodes in the cluster and shows their status, roles, age, and version.[1]

### 2. Run an NGINX Pod

```bash
k run nginx-pod --image=nginx
```

Creates a Pod named `nginx-pod` using the `nginx` image.[1]

### 3. List Pods

```bash
k get pods
```

Shows Pods in the current namespace along with readiness, status, restart count, and age.[1][2]

### 4. List Pods with node details

```bash
k get pods -o wide
```

Displays extended Pod information such as Pod IP, node name, and other scheduling details, which helps identify where Pods are running.[1]

### 5. Create resources from YAML

```bash
k create -f definition.yaml
```

Creates Kubernetes resources from the definitions written in a YAML manifest file.[2]

### 6. Describe a Pod

```bash
k describe pod <pod-name>
```

Shows detailed information about a Pod, including events, node assignment, container state, image, labels, and troubleshooting details.[1][4]

## Additional Useful Commands

These commands are commonly used along with the basics above.

### 7. Apply resources from YAML

```bash
k apply -f definition.yaml
```

Creates or updates resources from a YAML file. In day-to-day Kubernetes work, `apply` is often preferred for declarative management.[2]

### 8. View logs

```bash
k logs <pod-name>
```

Displays container logs from a Pod, which is useful for troubleshooting application issues.[2]

### 9. Delete a Pod

```bash
k delete pod <pod-name>
```

Deletes the specified Pod from the cluster.[2]

### 10. Get all common resources

```bash
k get all
```

Lists common resources in the current namespace, such as Pods, Services, Deployments, and ReplicaSets.[2]

### 11. Watch Pod status continuously

```bash
k get pods -w
```

Continuously watches Pod changes in real time, which is useful while creating or debugging workloads.[2]

### 12. Get Pod YAML

```bash
k get pod <pod-name> -o yaml
```

Prints the full YAML definition of a Pod, including metadata and status fields.[1]

### 13. Describe a node

```bash
k describe node <node-name>
```

Shows detailed information about a node, including capacity, allocatable resources, conditions, and the Pods scheduled on it.[1][4]

## Example YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```

This manifest defines a basic Pod running an NGINX container, and it can be created with `k create -f definition.yaml` or `k apply -f definition.yaml`.[2]

## Notes

- Pods are the smallest deployable units in Kubernetes and typically contain one or more containers.[2]
- Worker nodes run Pods, while the control plane manages scheduling and cluster coordination.[2][3]
- `kubectl describe` and `kubectl logs` are two of the most useful commands for debugging.[4][5]