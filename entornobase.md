## La instalación del entorno se realizó sobre una MV con Ubuntu Server 20.04 usando vagrant y VBox

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


