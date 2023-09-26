## Monitor Amazon EKS control plane metrics using AWS Distro for Open Telemetry (ADOT) and Amazon Grafana


bservability is essential for running production Kubernetes clusters. Monitoring Control plane metrics is equally important as monitoring your applications. Monitoring API server metrics can give you insights into control plane’s performance and help identify issues pro-actively. For example, API server metrics can help identify poorly written controllers that can overload API servers, affecting your applications’ availability. Similarly, collecting  etcd metrics can help monitor the etcd size and ensure the database limit is not exceeded that can result in cluster entering a read-only state.

EKS Control plane exposes a number of metrics through the metrics endpoint that refers to the /metrics HTTP API. In this blog post, we will use AWS Distro for OpenTelemetry (ADOT) to scrape these metrics and use Amazon Managed Grafana to visualize them. ADOT is an AWS distribution based on the Cloud Native Computing Foundation(CNCF) OpenTelemetry project . It offers the various advantages like, a native Kubernetes SD (service discovery) integration that can automatically discover and scrape metrics from K8s components, Native support for creating recording and alerting rules based on metrics etc. Amazon Managed Service Prometheus is a managed service from AWS which can reliably store the metrics scraped by prometheus and customers does not have to worry about scaling. Amazon Managed Grafana provides  visualization with  Pre-built panels and dashboards for visualizing Prometheus metrics.

By leveraging Prometheus and Grafana, we get an end-to-end platform for monitoring, alerting, and visualizing EKS control plane metrics. Prometheus' tight K8s integration scrapped with Grafana's rich visualizations provide observability into the health and performance of our clusters. In this post, we will monitor Amazon EKS control plane metrics using Amazon Managed Service for Prometheus and visualize them in Amazon Grafana. We will install the ADOT collector to scrape metrics from the Kubernetes API server and ingest them into Amazon Managed Service for Prometheus. We will then create recording and alerting rules based on the control plane metrics, and send notifications to an SNS topic when alerts trigger. Finally, we will create Grafana dashboards to visualize the control plane metrics.


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

