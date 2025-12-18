---

### 📄 `docs/03-install-argocd.md`

```markdown
# 🚀 Step 3: Install Argo CD

**Argo CD** is a GitOps continuous delivery tool for Kubernetes.

## 📘 Why?

Argo CD:
- Syncs your Git repository with Kubernetes
- Automates deployments using Git as the source of truth
- Great for learning real-world GitOps practices

## 📥 Install Argo CD

We install the official Argo CD manifests in a dedicated namespace:

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml