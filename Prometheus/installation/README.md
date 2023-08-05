# Prometheus Installation

Prometheus can be installed in many ways such as

- using helm charts
- using operators
- custom images (docker)
- volume mount

## Using helm charts

### Add helm REPO

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`

### Update helm REPO

`helm repo update`

### Installing chart

`helm install [RELEASE_NAME] prometheus-community/prometheus`

### Exposing Prometheus service to NodePort 

`kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext`

can also be accessed by editing the existing service in `kubectl get svc` - prometheus server 

which can be edited by using `kubectl edit svc <service-name>`

### Accessing Prometheus Server

Prometheus Server can be accessed using the IP of the cluster followed by the assigned `NODEPORT IP` 

eg- `192.168.42.9:32123`