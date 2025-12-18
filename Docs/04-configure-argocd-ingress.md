---

### 📄 `docs/04-configure-argocd-ingress.md`

```markdown
# 🌐 Step 4: Expose Argo CD with Ingress

Now we expose the Argo CD web UI using an Ingress rule and domain name: `argocd.local`

## 📘 Why?

By default, Argo CD is only accessible via port-forward or internal networking.

We use an Ingress so:
- We can access it via a real domain (argocd.local)
- Integrate it with HTTPS/TLS (later)
- Align with production-style setups

## 🛠️ Add `ingressClassName`

Kubernetes 1.19+ requires `ingressClassName` to route traffic properly.

## 📝 Ingress Manifest

```yaml
# manifests/argocd/ingress.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: argocd-ingress
  namespace: argocd
  annotations:
    nginx.ingress.kubernetes.io/backend-protocol: "HTTPS"
    nginx.ingress.kubernetes.io/ssl-redirect: "false"
spec:
  ingressClassName: nginx
  rules:
    - host: argocd.local
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: argocd-server
                port:
                  number: 443