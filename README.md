# nginx-observability-umbrella-chart

An umbrella charts that installs a nginx web server + Prometheus & Grafana for scraping and monitoring.

## Pre-req installations:

 1. Helm 3.
 2. K8s Cluster.
 3. Kubectl Client CLI

## Installation:

 1. Clone the repo using:
 `git clone https://github.com/asafMeytal/nginx-observability-umbrella-chart.git`
 2. Navigate to the folder and install the dependencies charts using:
   ```
  cd nginx-observability-umbrella-chart
  helm dependency build
  ```

3. Install the helm chart:<br>
`helm install observability-umbrella . -n <namespace> --create-namespace`

## View Grafana Nginx Dashboard
To view the Grafana Dashboard of the Nginx service you should port-forward the traffic of the grafana service, and navigate locally:

1. Port-forward with:
`kubectl port-forward svc/observability-umbrella-grafana 3000:80`
2. Navigate to:
    http://localhost:3000/
 
 3. Login with admin/admin user+pass.
 4. Navigate to the Nginx Dashboard.

## Notes:
1. Chart will be installed in the current K8s cluster.
2. Nginx  is set to 3 replicas, with HPA + PodDisruptionBudget + Affinity. Please refer to comments in the `values.yaml` file.