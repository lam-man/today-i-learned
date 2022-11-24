# Architecture and Theory

## Big picture view 

### Container
Isolated area of an OS with resources usage limits applied 
- Control Groups
- Namespaces

## Kernel Primitives
### Namespaces 
Mainly for isolation

- Linux namespaces
  - Process ID (pid)
  - Network (net)
  - Filesystem/mount (mnt)
  - Inter-proc comms (ipc)
  - UTS (uts) --> Host name
  - User (user)--> The root user of a contianer will be mapped to an unpreviliged user in host. 


### Control Groups 
Grouping objects and setting limits. Useful in control noisy neighbors.

## Docker Engine


## Windows spotlight

## ToDos
- [ ] Read [Linux Control Groups](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/resource_management_guide/ch01)
- [x] Read [Linux Namespace](https://www.nginx.com/blog/what-are-namespaces-cgroups-how-do-they-work/)