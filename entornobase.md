## La instalación del entorno se realizó sobre una MV con Ubuntu Server 20.04 usando vagrant y VBox con 2 CPU y 20GB de Disco. Particularmente tuve que hacer un lvextend del disco ya que era más pequeño del requerido por minikube. 

### 1.- Instalación de GIT

```
add-apt-repository ppa:git-core/ppa
apt update
apt install git

```

#### Se valida la versión instalada

```
git --version
git version 2.38.1
```

##### https://github.com/

### 2.- Instalación de Kubectl

```
curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl
curl -LO https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

#### Se valida la versión instalada
```
kubectl version –short
kubectl version --output=yaml
```
##### https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/


### 3.- Instalación de AWS-CLI:

```
curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
unzip awscli-bundle.zip
python3 awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
```

#### Se valida la versión instalada
![image](https://user-images.githubusercontent.com/67799058/199109819-1e66c107-ba4d-4e43-89da-e470ac760a31.png)

### 4.- Instalación de eksctl:

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
```
#### Se valida la versión instalada
```
eksctl version
```
![image](https://user-images.githubusercontent.com/67799058/199109979-6fe1fbee-ae03-423f-b1fb-89a8b7c36b1d.png)

##### https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html

### 5.- Instalación de Docker:
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt install docker-ce
```
```
sudo systemctl status docker
```

![image](https://user-images.githubusercontent.com/67799058/199110239-dbb04970-d0ab-44e6-8997-330d66d0d0fa.png)

```
#### Se valida la versión instalada
```

![image](https://user-images.githubusercontent.com/67799058/199110260-4c7a976b-ecaa-4ad0-a1b9-acd17e8ba18f.png)

#### Nota: Se deben realizar los siguientes pasos adicionales: 

```
sudo groupadd docker 
sudo usermod -aG docker
newgrp docker
```

### 6.- Instalación de Minikube:
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
install minikube-linux-amd64 /usr/local/bin/minikube
```

#### Iniciamos Minikube indicando que usaremos a Docker como runtime

![image](https://user-images.githubusercontent.com/67799058/199111547-e0c75c9d-c8bc-4863-8da1-880f9a35384e.png)


#### Se valida la versión instalada

![image](https://user-images.githubusercontent.com/67799058/199111776-0766b37e-efe8-4580-9556-d5c4ec1a3d4f.png)


#####https://minikube.sigs.k8s.io/docs/start/

