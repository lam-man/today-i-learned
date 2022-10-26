# Kubernetes Ingress Notes

This document focus on the K8s ingress. Contents will be show in the question format. I am trying to understand ingress by answering those questions.

## Relationship between Ingress Controller, Ingress and Ingress Rules
I was so confused by the relationship between these three elements until I see the explanation from [StackOverflow](https://stackoverflow.com/a/60701977).

Ingress : Object with a set of routing rules. (In OSM, the rules are defined in the IngressBackend YAML file.)
Ingress Controller: Running pods in a K8s cluster. (For example, Web Application Routing has Nginx running in namespace app-routing-system.)

Metaphorical explanation:
Ingress -> A gun.
Ingress Controller -> A soldier. (Capable to pull the trigger of the gun)
Ingress Rules -> Person who commands the soldier to where to shoot. (Ingress rules indicate where is the destination.)