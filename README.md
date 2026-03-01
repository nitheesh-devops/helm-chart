# 🚀 Hands-on Practice: Helm Chart Deployment on AWS EKS

Today I completed hands-on practice on **Helm** and deployed an application on **AWS EKS**.  
In this Proof of Concept (POC), I explored how Helm works and how it simplifies Kubernetes application management.

Below, I am explaining the complete step-by-step implementation.

---

## 📌 Project Overview

The main goal of this mini project was to understand:

- Helm chart structure
- Dynamic configuration using `values.yaml`
- Helm install, upgrade, and rollback
- Release versioning
- Pushing the project to GitHub

---

## 🛠 Tools Used

- AWS EKS
- Helm
- kubectl
- Git
- GitHub

---

## 🧠 What is Helm?

Helm is a **package manager for Kubernetes**.

Just like we use:
- `apt` for Linux
- `npm` for Node.js

Helm helps us:

- Define Kubernetes applications using reusable templates (charts)
- Manage configurations easily
- Perform version upgrades
- Rollback to previous versions if something breaks

Helm makes Kubernetes deployments more structured and manageable.

---

# 🏗 Step-by-Step Implementation

---

## 1️⃣ Created EKS Cluster

I created an EKS cluster in AWS to deploy my Helm application.

After completing the practice, I deleted the cluster to avoid unnecessary AWS billing.

---

## 2️⃣ Installed Helm

Installed Helm from the official documentation:

https://helm.sh/docs/intro/install/

Verified installation:

```bash
helm version
```

---

## 3️⃣ Created Helm Chart

Created a new Helm chart:

```bash
helm create helmapp
```

Checked the directory structure:

```bash
tree helmapp
```

This generated the default Helm chart structure including:

- Chart.yaml
- values.yaml
- templates/
- deployment.yaml
- service.yaml

---

## 4️⃣ Modified Templates

Inside the `templates/` folder:

- Edited `deployment.yaml`
- Edited `service.yaml`

Made replica count dynamic using:

```yaml
replicas: {{ .Values.replicaCount }}
```

---

## 5️⃣ Updated values.yaml

Configured dynamic values in `values.yaml`:

```yaml
replicaCount: 3
```

Also updated image and service configurations as needed.

---

## 6️⃣ Updated Chart.yaml

Updated basic metadata:

- Chart name
- Version
- Description

---

## 7️⃣ Installed Helm Release

Installed the Helm chart:

```bash
helm install helmapp ./helmapp
```

Verified release:

```bash
helm list
```

---

## 8️⃣ Upgraded Helm Release

Changed replica count in `values.yaml`:

From:

```yaml
replicaCount: 3
```

To:

```yaml
replicaCount: 5
```

Upgraded the release:

```bash
helm upgrade helmapp ./helmapp
```

Checked release history:

```bash
helm history helmapp
```

---

## 9️⃣ Rolled Back to Previous Version

Rolled back to previous release:

```bash
helm rollback helmapp 1
```

Verified rollback:

```bash
helm history helmapp
```

This helped me understand how Helm manages release versions.

---

## 🔟 Pushed Project to GitHub

Installed Git and executed:

```bash
git init
git status
git add .
git commit -m "Helm mini project"
git branch -M main
git remote add origin <your-github-repo-link>
git push -u origin main
```

Authentication was done using GitHub Personal Access Token.

---

# 📜 Helm Commands Used

```bash
helm create helmapp
helm install helmapp ./helmapp
helm upgrade helmapp ./helmapp
helm history helmapp
helm rollback helmapp <revision>
helm list
```

---

# 🧹 Cleanup

After completing the practice, I deleted the EKS cluster to avoid unnecessary AWS billing.

---

## 💡 Key Learnings

- Helm simplifies Kubernetes application management.
- `values.yaml` allows dynamic configuration.
- Helm makes upgrades and rollbacks very easy.
- Release versioning is powerful for production environments.
- Managing deployments through Helm improves structure and control.

---

✅ This hands-on practice helped me clearly understand Helm release lifecycle and version management.

---

# 👨‍💻 Author

**Nitheesh Kumar Bellamkonda**  
DevOps Engineer  

---

# 🧰 Tool Stack

- AWS EKS
- Kubernetes
- Helm
- kubectl
- Git
- GitHub
- Linux

---

⭐ If you found this project helpful, feel free to connect or explore more of my repositories.
