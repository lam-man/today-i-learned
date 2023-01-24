# Observability: Telemetry and Logs

The injected sidecar proxy intercept the traffic and **collect metrics.**
- Sidecar deployment allows collecting metrics
- Metrics give visibility into the state of the system
  - Understand waht's happening, troubleshoot, maintain, and optimize apps
- Telemetry:
  - Metrics
  - Distributed traces
  - Access logs

## Metrics - 4 golden signals
### Overview
- Latency: the time it takes to service a request
- Traffic: how much demand is placed on the system
  - RPS
- Errors: rate of failed requests
  - Http 500
- Saturation: how full the most constrained resources of service are
  - Threadpool utilization

### Different level of metrics
- Proxy-level metrics
  - Traffic passing through the proxy
  - Lowest granularity (e.g., metrics on individual listeners,   clusters)
  - Operators control which metrics are generated/collected at each   workload instance
  - Exposed from the /stats endpoint on the proxy
- Service-level metrics
  - Cover the four golden signals
  - Monitor service-to-service communication
  - Come with dashbaords
  - Customizable by the operators
- Control plane metrics 
  - Monitoring the situation of Istio itself (not user services)
  - Examples:
    - number of conflicting inbound/outbound listeners
    - number of clusters without instances
    - rejected or ignored configurations

## Observability Tool
### Prometheus
- [ ] How to install prometheus with Istio?
  - Install from /samples/addons
    - `istio dashboard prometheus`
- [ ] How to see the dashboard?
- [ ] How to show the metrics?
- [ ] How to bring your own Prometheus?
- [ ] What is the Prometheus metrics emit port for Istio?
- [ ] What components of Istio will emit the metrics?
  - Istiod
  - Istio Gateway
  - Istio Operator

## Grafana
- Open platform for analytics and monitoring
- Connects to Prometheus (and other sources)
- Monitor health of Istio and apps in the mesh
- Install from `/samples/addons` folder
  - `istioctl dashboard grafana`

:warning: **You have to deploy Prometheus before Grafana.**

## Distributed Tracing with Zipkin
- Trace: collection of spans
- Span: name, start/finish timestamp, tags, context
- Tags: applied to all spans used for querying/filtering
- Spans are sent to the collector to validate, index & store the data

- Examples:
  - istio.mesh_id
  - istio.canonical_service
  - upstream_cluster
  - http.url
  - http.status_code
  - zone

- Install from `/samples/addons/extras` folder
  - `istioctl dashboard zipkin`






## Questions
- [ ] How to get the metrics?
- [ ] How to see the traces?
- [ ] How to access logs?

## References
- [Istio Observability](https://istio.io/latest/docs/concepts/observability/)
