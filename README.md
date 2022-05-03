# Aplicação de Modelo SRE

Instalação do Rancher Desktop via pacote deb Ubuntu 

Installation via .deb Package
Add the Rancher Desktop repository and install Rancher Desktop with:

```
curl -s https://download.opensuse.org/repositories/isv:/Rancher:/stable/deb/Release.key | gpg --dearmor | sudo dd status=none of=/usr/share/keyrings/isv--rancher-stable-archive-keyring.gpg
echo 'deb [signed-by=/usr/share/keyrings/isv-rancher-stable-archive-keyring.gpg] https://download.opensuse.org/repositories/isv:/Rancher:/stable/deb/ ./' | sudo dd status=none of=/etc/apt/sources.list.d/isv-rancher-stable.list
sudo apt update
sudo apt install rancher-desktop
```

Instalação da aplicação no kubernetes via Helm 

```
$ cd k8s/helm
$ kubectl create ns robot-shop
$ helm install robot-shop --namespace robot-shop .

```

# Monitoramento - Prometheus e Grafana

Para subir a stack de Monitoramento no kubernetes 
Acesse a raiz do repositorio e Execute:

```
$ cd monitoring

$ kubectl create namespace monitoring

$ kubectl create -f k8s-prometheus/clusterRole.yaml
$ kubectl create -f k8s-prometheus/config-map.yaml
$ kubectl create -f k8s-prometheus/prometheus-deployment.yaml --namespace=monitoring
$ kubectl create -f k8s-prometheus/prometheus-service.yaml --namespace=monitoring

$ kubectl apply -f kube-state-metrics/
$ kubectl create -f k8s-grafana/

```

# Logging - Loki
Para subir a stack de Log no kubernetes


```
$ helm repo add grafana https://grafana.github.io/helm-charts
$ helm install loki grafana/loki-stack --namespace monitoring --create-namespace --set grafana.enabled=true
