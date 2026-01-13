# Enforce Automated K8s cluster security using "kyverno policy generator" and "argocd"

High Level Design
On a very high level, A DevOps Engineer will write the required Kyverno Policy custom resource and commits it to a Git repository. Argo CD which is pre configured with auto-sync to watch for resources in the git repo, deploys the Kyverno Policies on to the Kubernetes cluster.

<img width="1575" height="626" alt="image" src="https://github.com/user-attachments/assets/bf05082a-724d-495e-a025-9e7adc986734" />


Step 1:
- Create an EKS Cluster on AWS.
- In this case, I have created an EKS cluster using eksctl tool with the following configurations.
- command: eksctl create cluster --name kyverno-cluster --region us-east-1 --nodegroup-name kyverno-nodegroup --node-type t3.small --nodes 3