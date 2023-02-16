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

## Kubernetes Object Management


## ToDo
- [ ] You may want to reade the [kubectl book](https://kubectl.docs.kubernetes.io/guides/)