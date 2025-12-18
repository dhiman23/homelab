---

### 📄 `docs/05-access-argocd.md`

```markdown
# 🧪 Step 5: Access Argo CD via argocd.local

Let’s make `https://argocd.local` work in your browser and CLI.

## 🧩 Step 1: Update `/etc/hosts`

Since we don’t have a real DNS, map the domain manually:

```bash
echo "127.0.0.1 argocd.local" | sudo tee -a /etc/hosts