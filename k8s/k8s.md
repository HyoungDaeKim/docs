### java
```
sudo apt update
sudo apt install unzip
sudo apt install zip
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk list java
sdk install java 11.0.3.hs-adpt
```
### wsl
* root / root
* ubuntu / ubuntu
* minikube
```
wsl --list --verbose

useradd -m -G sudo -s /bin/bash "ubuntu"
passwd "ubuntu"

tee /etc/wsl.conf <<_EOF
[user]
default=ubuntu
_EOF

wsl --terminate Ubuntu22
wsl
```
### k8s alias
```
# kubctl
alias k='kubectl'
source <(kubectl completion bash)
complete -o default -F __start_kubectl k

alias goprjt='cd /home/muzel/Project/ideaProjects'

alias ms='minikube start'
```
### minikube
* minikube의 설정 및 command 확인
```
minikube docker-env
```
* minikube docker-daemon 과 연결
```
eval $(minikube -p minikube docker-env)
```

```
./gradlew clean build -x test
docker login
docker build --tag cas/cas-auth .
docker build --tag muzel/test:0.0.8 .
docker push muzel/test:0.0.8
docker images
minikube image ls
minikube image load muzel/test:0.0.8

kubectl delete deployment cas-auth
kubectl apply -f k8s/deployment.yaml
kubectl get pods

docker run -e "IP=0.0.0.0" -e "BIND_ADDRESS=0.0.0.0" -e "INITIAL_PORT=7001" -e "MASTERS=3" -e "SLAVES_PER_MASTER=0" -p 7001-7003:7001-7003 --name redis-cluster-3 grokzen/redis-cluster:7.0.15

kubectl port-forward <your pod name> 5005:5005

kubectl exec cas-auth-b77dd4979-7nx76 -it -- bash

kubectl delete service cas-auth
kubectl apply -f k8s/service.yaml

minikube service cas-auth

kubectl create namespace sample
kubectl config set-context --current --namespace sample

kubectl get events --all-namespaces
kubectl config set-context $(kubectl config current-context) --namespace=sample
```
