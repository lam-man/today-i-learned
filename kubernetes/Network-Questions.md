# Questions on Kubernetes Networking

- [X] For services with Cluster IP, how they accept incoming request from the load balancer type request (ingress/ingress controller) and pass it to the pods?
  - :warning: **Answer from ChatGPT. Need to verify the correctness.**: In a cluster with Istio installed, the Istio ingress gateway will accept the traffic first and use the load balancing algorithm specified in its configuration to distribute the traffic to the correct service. Then the Envoy proxy running in the pod of the service will use the routing rules defined in the virtual service to determine the correct destination for the request and forward it accordingly.
- [X] Relationship between `Istio ingress gateway`, `Istio gateway`, `Istio Virtual Service` and `Istio Destination Rules`. 
  - `Istio gateway` is used to config `Istio ingress gateway`. For example, which port `ingress gateway` should listener to. 
  - `Istio Virtual Service` is used to config envoy proxy, which is `proxy v2` in Istio. For example, virtual service tell which destination a request should be routed to. 
  - `Destination rules`:
    - Istio destination rules define how traffic is routed to different versions of a service within a service mesh. They are used to specify the subsets of service instances that traffic should be sent to, based on factors such as traffic weighting, connection pool size, and circuit breaking rules. 
    - When a client makes a request to a service, the Envoy proxy intercepts the request and checks the destination rules to determine which version of the service should handle the request. This is done by matching the request's host and path to the host and path specified in the destination rule.
    - Once a match is found, the Envoy proxy uses the weight specified in the destination rule to determine how much traffic should be sent to each subset of instances. For example, if one subset has a weight of 90 and another has a weight of 10, the Envoy proxy will send 90% of the traffic to the first subset and 10% to the second.
    - Istio destination rules can also be used to configure advanced features like connection pool size, circuit breaking, and timeout settings. These settings allow you to control the behavior of the service and handle situations like high traffic or service outages.
- [ ] How `iptables` got used by envoy? 
- [ ] How `iptables` works for traffic routing?
- [X] L4 load balancer will not touch data, then how the backend servers know how to decrypt it?
  - Nope. LB does nothing except message (request) forwarding. At the very beginning (hand shake step), LB will have a backend server to establish the connection. Then, all the information change are between client and the specific backend server. LB just transfer the information using NAT.
  - LB are transparent between client and server.