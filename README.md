# Atualizar Sistema Operacional
```
sudo apt update
sudo apt upgrade
```

# Instalar pacotes adicionais
```
sudo apt install bash-completion
sudo apt install tree
```

# Instalar Docker
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

# Executar Docker com usuário sem privilégios

```
sudo groupadd Docker
sudo usermod -aG docker $USER
newgrp docker
```

# Ativar inicialização automática do serviço do Docker
```
sudo systemctl enable Docker
```

# Instalar Minikube

```
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

# Inicializar Cluster (1 Master + 2 Workers)

```
minikube start --nodes 3 -p mycluster
```

# Instalar Kubectl

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```

# Configurar Auto-complete do Kubectl (bashrc)
```
alias k='kubectl'                 # Atalho para kubectl
alias kg='kubectl get'            # Atalho para kubectl get
alias kga='kubectl get all'       # Atalho para kubectl get all
alias kd='kubectl describe'       # Atalho para kubectl describe
alias ka='kubectl apply -f'       # Atalho para kubectl apply -f
alias kdel='kubectl delete'       # Atalho para kubectl delete
alias kex='kubectl exec -it'      # Atalho para kubectl exec -it
alias kl='kubectl logs'           # Atalho para kubectl logs
alias kctx='kubectl config use-context'  # Trocar o contexto
alias kns='kubectl config set-context --current --namespace'  # Trocar o namespace atual
source ~/.bashrc		  # Recarregar Bash
```
