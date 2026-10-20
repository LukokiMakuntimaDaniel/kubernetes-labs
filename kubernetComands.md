# Kubernetes CLI – Comandos Essenciais

> Referência rápida de comandos `kubectl` para gestão, configuração, execução e monitorização de recursos num cluster Kubernetes.

---

## 1. Versão e Configuração do Cluster

### `kubectl version`
Mostra a versão do cliente kubectl e do cluster Kubernetes.

### `kubectl config get-clusters`
Lista os clusters Kubernetes configurados no kubectl.

### `kubectl config get-contexts`
Apresenta os contextos configurados, incluindo clusters, utilizadores e namespaces associados.

---

## 2. Gestão de Pods

### `kubectl get pods`
Lista os pods existentes no namespace atual.

### `kubectl get pods -o wide`
Lista os pods com informações adicionais, como endereço IP, nó associado e estado.

### `kubectl describe pod hello-world`
Apresenta informações detalhadas do pod `hello-world`, incluindo configurações, eventos e possíveis erros.

### `kubectl delete pod hello-world`
Remove o pod `hello-world` do cluster.

---

## 3. Variáveis de Ambiente

### `export MY_NAMESPACE=sn-labs-$USERNAME`
Define a variável de ambiente `MY_NAMESPACE`, utilizando o nome do utilizador atual para identificar o namespace.

---

## 4. Construção e Publicação de Imagens Docker

### `docker build -t us.icr.io/$MY_NAMESPACE/hello-world:1 . && docker push us.icr.io/$MY_NAMESPACE/hello-world:1`
Constrói a imagem Docker a partir do diretório atual e publica-a no IBM Cloud Container Registry.

---

## 5. Criação e Execução de Pods

### `kubectl run hello-world --image us.icr.io/$MY_NAMESPACE/hello-world:1 --overrides='{"spec":{"template":{"spec":{"imagePullSecrets":[{"name":"icr"}]}}}}'`
Cria um pod chamado `hello-world`, utilizando uma imagem do IBM Cloud Container Registry e configurando as credenciais necessárias para descarregá-la.

---

## 6. Gestão de Recursos com Ficheiros YAML

### `kubectl create -f hello-world-create.yaml`
Cria recursos Kubernetes com base nas definições presentes no ficheiro YAML.

### `kubectl apply -f hello-world-apply.yaml`
Cria ou atualiza recursos Kubernetes de acordo com as definições do ficheiro YAML.

---

## 7. Deployments e Services

### `kubectl get deployments`
Lista os deployments existentes no namespace atual.

### `kubectl expose deployment/hello-world`
Cria um Service para disponibilizar o deployment `hello-world` através da rede interna do cluster.

---

## 8. Acesso à API Kubernetes

### `kubectl proxy`
Inicia um proxy local que permite aceder à API do Kubernetes através do endereço `localhost`.

---

**Nota:** Os comandos apresentados servem como referência rápida para operações comuns de administração e gestão de recursos Kubernetes.