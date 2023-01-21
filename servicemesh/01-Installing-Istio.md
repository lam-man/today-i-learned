# Installing Istio

## Installing Profile

The differences between profiles are the components that will be intalled in a cluster.
- default
  - production usage
- demo
  - mainly for learning and explore istio features
- empty
- minimal
  - install ingress or ingress gateways later
- preview
- remote

## Installing using `istioctl`
Installing a certain istio versio in your cluster. The version will be the same to your `istioctl` version.

- Command
  `istioctl install --set profile=demo`

## Installing using `istio-operator`

## Discovery Selectors

## Lab
- Step 1: Download Istio
  - Without version specify:
    - `curl -L https://istio.io/downloadIstio | sh -`
  - With version specified:
    - `curl -L https://istio.io/downloadIstio | ISTIO_VERSION=1.16.1 TARGET_ARCH=x86_64 sh -`
- Step 2: Using `istioctl` from the download version
  - Go to the downloaded istio folder
    - `cd /home/wen/learn/Istio/istio-1.16.1`
  - Set the istioctl to use 
    - `export PATH=$PWD/bin:$PATH`
  - Verify the version of `istioctl`
    - `istioctl version`
- Step 3: Installing
  - Show profiles
    - `istioctl profile list`
  - Deploy `istio-operator`
    - `istioctl operator init`
  - Installing
    - `kubectl apply -f demo-profile.yaml`
  - Check the `istio-operator` resource status
    - `k get istiooperator -A`
    - `k get iop -A`
- Step 4: Sidecar injection
  - Automatic sidecar injection
    - `k label namespace default istio-injection=enabled`
    - Remove label
      - `k label namespaces default istio-injection-`
    - Overwrite label
      - `k label namespace default istio-injection=disabled --overwrite=true`
  - Check namespaces with sidecar injection
    - `k get namespace -L istio-injection`
- Step 5: Create deployment to see how proxy got injected
  - Create nginx deploy
    - `k create deploy my-nginx --image=nginx`
- Step 6: Update istio-operator
  - Add egress
    - `k apply -f egress.yaml`
- Step 7: Remove istio resources
  - `istioctl operator remove`
  - `istioctl uninstall --purge`

## Questions
- What is the `istiooperator` CRD? 
  - Functions
  - How it control the upgrade of Istio?

## References
- [Using the Istioctl Command-line Tool](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/)

