# Deploy with Helm
This doc focus on how to deploy an application using helm.

## Create a helm chart 
The following command will create the boiler templates for helm chart.
- Command `helm create <chart-name>`

- Files in detail
  ├── charts # Empty folder for sub charts that are dependencies for main chart.
  ├── Chart.yaml # High level information of the chart. More like a meta data section: type, version, apiVersion ...
  ├── templates
  │   ├── deployment.yaml
  │   ├── _helpers.tpl
  │   ├── hpa.yaml
  │   ├── ingress.yaml
  │   ├── NOTES.txt # Display in the terminal when someone download and install this chart
  │   ├── serviceaccount.yaml
  │   ├── service.yaml # Kubernetes service menifest
  │   └── tests
  │       └── test-connection.yaml
  └── values.yaml # Fields to configure the K8s objects like pod, deployment, service. For example, config the image and image pull policy.

## Check the changes of template changes in local
- Command `helm template first-chart .`
- Command to upgrade the changed chart: `helm upgrade first-chart .`

## Rollback with helm
- Get all the versions
  Command: `helm history first-chart`
- Rollback to the most recent version 
  Command: `helm rollback first-chart`
- Rollback to a specific version 
  Command: `helm rollback first-cahrt <version-number>`