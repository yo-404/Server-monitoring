# Installation - Prometheus

### Why prometheus

Server monitoring in Kubernetes (k8s) is essential for maintaining the health, performance, and availability of your applications and infrastructure. Kubernetes provides various tools and methods to monitor the cluster and its components .Prometheus is a widely used open-source monitoring solution that is native to Kubernetes. It allows you to collect and store time-series metrics data from different components within your cluster. You can set up exporters to scrape metrics from various sources like Kubernetes API server, nodes, containers, etc. 

Prometheus is an open-source monitoring and alerting system that helps you collect and store metrics about your software systems and infrastructure, and analyze that data to gain insights into their health and performance. It provides a powerful query language, a flexible data model, and a range of integrations with other tools and systems. With Prometheus, you can easily monitor metrics such as CPU usage, memory usage, network traffic, and application-specific metrics, and use that data to troubleshoot issues, optimize performance, and create alerts to notify you when things go wrong.

Additionally, Prometheus provides a powerful query language (PromQL) for analyzing and visualizing the collected data. Also with the help of Visualization tools like grafana the data can be visualizaed in form of a dashboard which is easy to understand .


### Why monitoring 

Monitoring your Kubernetes cluster is essential for ensuring the health and performance of your applications and infrastructure. Here are some reasons why monitoring your Kubernetes cluster is important:

- Ensures High availability : By monitoring your cluster , you can set up alerts for uncertain events which ensures that your application remains available even in unexpected events

- Optimize Performance : Monitoring allows you to track the performance of your deployed application over time and identify the opportunities to optimize performance . By understanding the usage patterns and resource consumptions you can make informed decisions that will improve and optimize the performance of your application over time.

- Identifying issues and troubleshooting : Through the monitoring of your Kubernetes cluster, you can promptly detect problems like application failures, resource limitations, and network issues. Real-time monitoring allows you to address these problems proactively, preventing any negative impact on your users.

- Security and compliance: Monitoring your Kubernetes cluster can help you identify potential security risks and ensure compliance with regulations and policies. By tracking access logs and other security-related metrics, you can quickly detect and respond to potential security threats.


### Prometheus Architecture

![image](https://github.com/yo-404/Server-monitoring/assets/100558220/e6f82dc4-94c4-40fc-b608-1713fac3b867)


### Why Prometheus over other monitoring tools?

- Open Source:Prometheus is an open-source project that is free to use and has a large community of contributors. This means that you can benefit from ongoing development, bug fixes, and feature enhancements without paying for a commercial monitoring solution.

- Native Kubernetes Support (Part of CNCF) Eaasy to integrate with kubernetes and works seamlessly .Supports auto discovery of kubernetes services and pods

- Powerful query language : Comes with a powerful query language i.e. PROMQL that can be used to retrieve metrics data . Approprate query can be written in order to achieve desired result. 

- Scalalbilty: Supports multi-Node architectures and can handle large volumes of data with ease

- Integrations: Prometheus integrates with a wide range of other tools and systems, including Grafana for visualization, Alertmanager for alerting, and Kubernetes API server for metadata discovery.
