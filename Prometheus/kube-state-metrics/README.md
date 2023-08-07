# kube-state-metrics

which the isntallation of prometheus you will also get a service named kube-state-metrics . Kube-state-metrics is an open-source project in the Kubernetes ecosystem that serves as a bridge between Kubernetes and monitoring systems like Prometheus. It collects and exposes various metrics about the state of Kubernetes objects, such as pods, nodes, deployments, services, and more. These metrics provide insights into the health and performance of the Kubernetes cluster and the workloads running within it.

Here are some key points about kube-state-metrics:

- *Metrics Collection*: Kube-state-metrics interacts with the Kubernetes API server to retrieve information about the current state of various Kubernetes resources. It translates this information into Prometheus-compatible metrics.

- *Stateful Metrics*: Unlike Prometheus, which focuses on time-series data, kube-state-metrics focuses on the current state of Kubernetes objects. It provides metrics related to the number of replicas, status of pods (running, pending, failed), conditions of nodes, resource utilization, and other object-specific details.

- *Service Discovery*: kube-state-metrics automatically discovers and exports metrics for all relevant Kubernetes objects. This means that as new objects are created or existing ones change, the corresponding metrics will be updated and exposed to Prometheus for monitoring.

- *Integration with Prometheus*: kube-state-metrics is typically used alongside Prometheus to enable monitoring and alerting in Kubernetes clusters. Prometheus scrapes the metrics exposed by kube-state-metrics, stores them in its time-series database, and enables querying and alerting based on these metrics.

- *Cluster Monitoring*: By collecting and exposing metrics about various Kubernetes resources, kube-state-metrics enables better visibility and monitoring of the entire Kubernetes cluster. This is crucial for maintaining the health and performance of the cluster and diagnosing any issues that may arise.

- *Prometheus Operator Compatibility*: For those using the Prometheus Operator to manage their Prometheus deployment, kube-state-metrics is often recommended as a standard way to monitor Kubernetes objects.


## exposing kube-state-metrics 

`kubectl expose service prometheus-kube-state-metrics --type=NodePort --target-port=8080 --name=kube-state-metrics-external`

this will create a svc with Nodeport

### Accessing Kube-state-metrics

kube-state-metrics can be accessed using the IP of the cluster followed by the assigned `NODEPORT IP` port 

eg- `192.168.42.9:30153`

The queries provided in kube-state-metrics can be used inside prometheus to get the data . The same data can be visualized inside grafana .


# To add a new entry 

`kubectl get cm`

`kubectl edit cm prometheus-server`

add the information in the scrape-config 

```
- job_name:kube-state-metrics-entrypoint
  static_configs:
  - targets:
    - 192.168.42.9:30153  
```