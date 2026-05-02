This guide covers essential Kubernetes (K8s) concepts and kubectl commands for beginners. Focuses on nodes, pods, and basic cluster management.

K8s Architecture Overview
Worker Nodes: Run application workloads (containers/pods). Use multiple for high availability and scaling.

Master Node: Controls the cluster, schedules pods, and monitors all worker nodes.

Kubectl: Primary CLI tool to deploy, inspect, and manage apps on the cluster.

Quick Setup
Create a shortcut for faster typing:

bash
alias k=kubectl
Core Commands
k get nodes
Lists all nodes (master + workers) in the cluster with status.

k run nginx-pod --image=nginx
Creates and starts a single pod running the NGINX container.

k get pods
Shows all pods, their status (Running, Pending, etc.), and restarts.

k get pods -o wide
Detailed pod view including IP, assigned node, and resource usage.

k create -f definition.yaml
Deploys resources (pods, deployments, etc.) from a YAML file.

k describe pod <pod-name>
Detailed info on a specific pod: events, status, logs, and issues.

Essential Additional Commands
k get all
Overview of all resources: pods, services, deployments, etc.

k delete pod <pod-name>
Removes a specific pod (recreates if managed by deployment).

k logs <pod-name>
Views container logs for troubleshooting.

k expose pod/nginx-pod --type=NodePort --port=80
Creates a service to access the pod externally.

k get services
Lists services and their access ports/URLs.

k apply -f definition.yaml
Creates or updates resources declaratively (preferred over create).

Example Workflow
Check cluster: k get nodes

Deploy pod: k run nginx-pod --image=nginx

Verify: k get pods -o wide

Debug: k describe pod nginx-pod or k logs nginx-pod

Expose: k expose pod/nginx-pod --type=NodePort --port=80

Access: k get services

Pro Tips
Use k get pods -w to watch changes in real-time.

Save common YAML configs for repeatable deployments.

Always check k get nodes first—unhealthy nodes block pod scheduling.