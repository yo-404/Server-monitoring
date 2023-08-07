# Grafana Installation

Grafana can be installed in many ways such as

- using helm charts
- using operators
- custom images (docker)
- volume mount

## Using helm charts

### Add helm REPO

`helm repo add grafana https://grafana.github.io/helm-charts`

### Update helm REPO

`helm repo update`

### Installing chart

`helm install grafana grafana/grafana`

### Exposing Prometheus service to NodePort 

`kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext`

This can be also done via editing the service type inside the default present service for grafana 

Grafana can be accessed using the IP of the cluster followed by the assigned `NODEPORT IP` 

Note- ' Make sure to allow inbound traffic to access grafana on cloud service

eg- `192.168.42.9:32123`

# to get the default password for grafana 

`kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo`

the above command will give you the password for grafana where the username will going to be "admin"


## default template for grafana dashboard

- Add the data source for prometheus in grafana 
- In dashboard creation you can import the standard template 3662 or create graphs and table as per you requirements . Graphs can be created using PROMQL queries .



