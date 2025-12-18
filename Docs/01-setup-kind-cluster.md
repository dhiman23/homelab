# 🧱 Step 1: Setup Kind Cluster

We start by creating a local Kubernetes cluster using **Kind (Kubernetes IN Docker)**. It’s lightweight, fast, and great for local dev/testing.

## 📘 Why?

We use Kind because:
- It spins up K8s inside Docker containers
- Perfect for a homelab with limited resources
- Works great with Argo CD and Ingress setups

## 🔧 Cluster Config

We expose ports 80 and 443 on the host so our Ingress controller can forward HTTP/HTTPS traffic to services inside the cluster.

```yaml
# manifests/kind-cluster-config.yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
name: argocd-cluster
nodes:
  - role: control-plane
    extraPortMappings:
      - containerPort: 80
        hostPort: 80
      - containerPort: 443
        hostPort: 443