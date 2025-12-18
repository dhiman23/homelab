---

### 📄 `docs/02-install-nginx-ingress.md`

```markdown
# 🌐 Step 2: Install NGINX Ingress Controller

Ingress controllers route external HTTP/HTTPS traffic into Kubernetes services.

## 📘 Why?

Without an Ingress controller, we can’t expose services like Argo CD using domain names like `argocd.local`.

We use **NGINX** because:
- It’s stable, widely used
- Has great community support
- Works well with Kind and Argo CD

## 📥 Install NGINX

Use the official manifest built for Kind:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.9.4/deploy/static/provider/kind/deploy.yaml