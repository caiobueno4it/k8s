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

# Configurar Alias e Auto-complete (Kubectl e Terraform)
```
alias k='kubectl'                                                   # Atalho para kubectl
alias kg='kubectl get'                                              # Atalho para kubectl get
alias kga='kubectl get all'                                         # Atalho para kubectl get all
alias kd='kubectl describe'                                         # Atalho para kubectl describe
alias ka='kubectl apply -f'                                         # Atalho para kubectl apply -f
alias kdel='kubectl delete'                                         # Atalho para kubectl delete
alias kex='kubectl exec -it'                                        # Atalho para kubectl exec -it
alias kl='kubectl logs'                                             # Atalho para kubectl logs
alias kctx='kubectl config use-context'                             # Trocar o contexto
alias kns='kubectl config set-context --current --namespace'        # Trocar o namespace atual

alias tf='terraform'                                                # Alias geral para Terraform
alias tfi='terraform init'                                          # Inicializar o diretório do Terraform
alias tfp='terraform plan'                                          # Criar plano de execução
alias tfa='terraform apply'                                         # Aplicar mudanças
alias tfaa='terraform apply -auto-approve'                          # Aplicar automaticamente sem confirmação
alias tfd='terraform destroy'                                       # Destruir recursos
alias tfda='terraform destroy -auto-approve'                        # Destruir automaticamente sem confirmação
alias tfv='terraform validate'                                      # Validar a sintaxe dos arquivos Terraform
alias tff='terraform fmt -recursive'                                # Formatar os arquivos Terraform
alias tfsw='terraform state list'                                   # Alias para Terraform Show
alias tfs='terraform state list'                                    # Exibir os recursos do estado do Terraform
alias tfsr='terraform state rm'                                     # Remover manualmente recursos do estado do Terraform
alias tfo='terraform output'                                        # Exibir as saídas do Terraform
alias tfoj='terraform output -json'                                 # Exibir as saídas de forma legível para outros scripts
alias tfup='terraform providers lock'                               # Atualizar os provedores
alias tfver='terraform version'                                     # Exibir a versão do Terraform

# Habilitar kubectl auto complete
echo 'source <(kubectl completion bash)' >>~/.bashrc
echo 'complete -o default -F __start_kubectl k' >>~/.bashrc
source ~/.bashrc
```
