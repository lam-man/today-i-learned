# Install With Helm

## Find Available Chart on ArtifactHub
[ArtifiactHub](https://artifacthub.io/) is a place to find publick Kubernetes packages.

## Steps and Commands
- Add software into your repo
  `helm repo add bitnami https://charts.bitnami.com/bitnami`
- Update your repo to have the latest version 
  `helm repo udpate`
- List the repoes you have 
  `helm repo list`
- Install the chart in your cluster
  `helm install kube-state-metrics bitnami/kube-state-metrics -n metrics`
- Install the chart with customized parameter
  `helm install <release-name> bitnami/metrics-server --set apiService.create=true`
  Example: `helm install challenge-metrics-server bitnami/metrics-server --set apiService.create=true`
- Double check the helm chart has been installed
  `helm ls -n metrics`

## Pull and Extract the Charts
After adding the repo, you may want to get one of the charts in the repo. Following is the way to do it. 

- Pull chart in `.tgz` format 
  `helm pull bitnami/kube-state-metrics`
- Pull chart and extract in local 
  `helm pull bitnami/kube-state-metrics --untar`

## Push Charts to an Azure Container Registry
Documentation for helm in Azure Container Registry 
[Push and pull Helm charts to an Azure Continer Registry](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-helm-repos)

## Check the Charts use command `helm show`
`helm show` has different kinds: `chart`, `value`, `all`, `readme`, and `crds`.

## Upgrade with helm
- Sample command: `helm upgrade kube-state-metrics bitnami/kube-state-metrics --version <version-number>`

