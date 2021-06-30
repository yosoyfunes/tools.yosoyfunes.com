# kubernetes

### Install kubectl

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.18.9/2020-11-02/bin/linux/amd64/kubectl
chmod +x ./kubectl
mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
```

### Install kubectx

[https://github.com/ahmetb/kubectx](https://github.com/ahmetb/kubectx)


```bash
sudo apt install kubectx
```

### Install kubeselect

[https://github.com/fatliverfreddy/kubeselect](https://github.com/fatliverfreddy/kubeselect)


```bash
wget https://raw.githubusercontent.com/fatliverfreddy/kubeselect/master/kubeselect
chmod +x kubeselect
sudo mv kubeselect /usr/local/bin
```

### Install kubie

[https://github.com/sbstp/kubie](https://github.com/sbstp/kubie)


```bash
wget https://github.com/sbstp/kubie/releases/download/v0.13.1/kubie-linux-amd64
chmod +x kubie-linux-amd64
sudo mv kubie-linux-amd64 /usr/local/bin
```

### Install eksctl
```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
```

### Connect to Pod for debug

```bash
kubectl run -i --tty --rm debug --image=alpine --restart=Never -- sh
```

### Install Helm
```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
rm ./get_helm.sh
```

### kubectl Docker
```bash
docker run --rm -ti yosoyfunes/cbff-local
```

### multitool

[https://github.com/Praqma/Network-MultiTool](https://github.com/Praqma/Network-MultiTool)


```bash
kubectl run multitool --image=praqma/network-multitool
```

### minikube with k8s 

```bash
docker run --rm -ti --hostname minikube -w /data \
    --network minikube \
    -v $HOME/.minikube:$HOME/.minikube \
    -v $HOME/.kube/:/root/.kube \
    -v ${PWD}:/data yosoyfunes/cbff-local
```