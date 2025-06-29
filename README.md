# Helm-Upgrade

This is a bash automation script that helps upgrade Cloud deployments on Azure Kubernetes Service (AKS) using Helm.

It:
✅ Switches to the AKS cluster you specify
✅ Lists Helm app versions + namespaces
✅ Prompts you to select version & namespace
✅ Runs Helm upgrade
✅ Optionally increases client service memory

📂 Files
helm_upgrade_flow.sh — main script

⚙️ Usage
1️⃣ Clone your repo:

git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
2️⃣ Make the script executable: 
chmod +x helm_upgrade_flow.sh

3️⃣ Run the script:
./helm_upgrade_flow.sh

🖥 What the script does
✅ Asks: Enter AKS cluster name
✅ Switches kubectl context
✅ Lists Helm releases (helm list -A)
✅ Asks: Enter version and namespace (e.g., 242.4.0 namespace)
✅ Runs: helm upgrade --install ifs-cloud helm/cloud --version <version> --namespace <namespace> --reuse-values --timeout 15m
✅ Asks: Do you want to increase client service memory to 1500 MB?
✅ If yes: helm upgrade --install cloud helm/cloud --set services.minMemory=1500 --reuse-values --timeout 15m
📝 Example flow
💡 Welcome! This script will help you connect to an AKS cluster, view Helm app versions, and upgrade Cloud.

👉 Please enter the AKS cluster name (example: abc-aks): abc-aks

✅ Successfully connected to 'abc-aks'.

📋 Fetching Helm app versions and namespaces...
242.4.0 abcnacespace1
251.0.0 abcnacespace2

👉 Please copy-paste a line from above (format: "<version> <namespace>")
Enter version and namespace: 242.4.0 abcnacespace1

🚀 Starting Helm upgrade for Cloud...
...
📌 Requirements
✅ kubectl configured for AKS
✅ helm installed
✅ jq installed
