# Traffic Management

## Gateways

- Ingress Gateway
- Egress Gateway

Gateways can be configured using `Gateway Resource`
  - A yaml file to config gateway
  - Sample yaml 
    ```yaml
    apiVersion: networking.istio.io/v1alpha3
    kind: Gateway
    metadata:
      name: my-gateway
      namespace: default
    spec:
      selector:
        istio: ingressgateway
      servers:
      - port:
          number: 80
          name: http
          protocol: HTTP
        hosts:
        - dev.example.com
        - test.example.com
    ```

  - yaml anatomy
    - Exposure ports
      ```yaml'
      spec:
        ...
        - port:
            number: 80
      ```
    - Applied the configuration with `selector`
      ```yaml
      spec:
      selector:
        istio: ingressgateway
      ```
    - Incoming reuqest filter, only the certain request resources will be accepted
      ```yaml
      hosts:
        - dev.example.com
        - test.example.com
      ```
- [ ] How to config?

## Simple Traffic Routing

To expose a service in the cluster, we have to bind a virtual service to it.
- [ ] So the virtual service is the ingress we are using in OSM?
  - Virtual Service expose the entire service in a cluster or expose a service to other service in the cluster? 
  - What are the differences between Istio VirtualService and k8s `service`? [k8s service](https://kubernetes.io/docs/concepts/services-networking/service/)
  - **My Understanding:**
    - Istio Gateway: ingress controller
      - Defines the allowed request resource/origin
    - Istio VirtualService: ingress backend
      - Defines the destination that request will be sent to
      - When the allowed request resource matches the destination, then the request will be routed to the target service.

## Destination Rule


## References
- [Istio Traffic Management](https://istio.io/latest/docs/concepts/traffic-management/)