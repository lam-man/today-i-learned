# Working with Kubernetes Objects

## Understanding Kubernetes Objects

### Object `spec` and `status`
- spec: its desired state
- status: current state of the object

### Required fields
When create a k8s object using a `yaml` file, following fields will have to be present:
- `apiVersion` - Which version of the Kubernetes API you're using to create this object
- `kind` - What kind of object you want to create
- `metadata` - Data that helps uniquely identify the object, including a name string, UID, and optional namespace
- `spec` - What state you desire for the object

## Labels and Selectors
### Label selectors
Labels are not unique to each object. Basically, a label can identify a a set of objects. Two types of selectors are supported by the current API: equality-based and set-based. Multiple requirements can be combined into one label selector. With multiple requirements, the comma is used to separate each other and :exclamation: **works as a logical AND (&&) operator**.

### Equality-based requirement
Label selectors support two types of equality-based requirements:
- `=`, `==`
  - The `=` and `==` operators are functionally equivalent. 
- `!=`. 
  - The `!=` operator renders an object ineligble for selection if the key exists with a value that matches the specified string.
- Example 
  ```
    environment = production
    tier != frontend
  ```

### Set-based requirement
Set-based label requirements filter keys according to a set of values. Three set-based requirements are supported: `in`, `notin` and `exists`. 

- `in` 
  - `environment in (production, qa)`
- `notin`
  - `tier notin (frontend, backend)`
- `exists`
  - `partition`
  - `!partition`
- `,` is used to separate multiple values and works as an logical `AND` operator.
  - `partition, environment in (production, qa)`

## Namespaces
Namespaces is used to isolate resources in a cluster. 
- Names of resources need to be unique within a namespace, but not across namespaces. 
- :exclamation: Ports within a namespace are unique, but not across namespaces.
- Namespace-based scoping is applicable only for namespaced objects. (e.g. Deployment, Service, etc.) Will not work for cluster-wide objects (e.g. StorageClass, Node, PersistentVolume, etc.)


## ToDo
- [ ] You may want to reade the [kubectl book](https://kubectl.docs.kubernetes.io/guides/)