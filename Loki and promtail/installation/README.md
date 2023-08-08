# Install Loki and Promtail using Docker

### Download Loki Config

```
wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml
```

### Run Loki Docker container

```
docker run -d --name loki -v $(pwd):/mnt/config -p 3100:3100 grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml
```

### Download Promtail Config

```
wget https://raw.githubusercontent.com/grafana/loki/v2.8.0/clients/cmd/promtail/promtail-docker-config.yaml -O promtail-config.yaml
```

### Run Promtail Docker container

```
docker run -d --name promtail -v $(pwd):/mnt/config -v /var/log:/var/log --link loki grafana/promtail:2.8.0 --config.file=/mnt/config/promtail-config.yaml

```

# using helm chart

```
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```

### deployment in custom namespace

`helm upgrade --install loki --namespace=loki-stack grafana/loki-stack`

The chart loki-stack contains a pre-configured Grafana, simply use `--set grafana.enabled=true`

### To get the admin password for the Grafana pod, run the following command

`kubectl get secret --namespace <YOUR-NAMESPACE> loki-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo`

To access the Grafana UI, run the following command:

`kubectl port-forward --namespace <YOUR-NAMESPACE> service/loki-grafana 3000:80`

or you can expose the ip and create a new service for external accessing with Nodeport IP  which can be accessed with given nodeport *PORT*