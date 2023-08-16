# Instalar kubectl

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
```

# Configurar auto-completar kubectl
```
source <(kubectl completion bash) # configura o autocomplete na sua sessão atual (antes, certifique-se de ter instalado o pacote bash-completion).

echo "source <(kubectl completion bash)" >> ~/.bashrc # add autocomplete permanentemente ao seu shell.
```

# Criar alias para o kubectl
```
alias k=kubectl
complete -F __start_kubectl k
```

# Instalar Kind
```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.14.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
curl -fsSL https://get.docker.com | bash
```

# Criar cluster Kind
```
kind create cluster (Basic)

kind create cluster --name <NameCluster> --config <FileName>.yml (Advanced)
```
