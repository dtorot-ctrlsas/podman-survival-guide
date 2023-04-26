# NOTES
+ Containers use namespaces(isolate processes) and cgroups(resource management: CPU time allocation, memory) kernel features
+ From the OCI (Open Container Initiative) there is an application specification
+ Container Images: immutable data that defines an app and its libraries (img-spec)
+ Container Instances: created from container images, the executable version (include network,disks,etc runtime necessities)(runtime-spec)
+ Software management
  + virtual machines (hypervisors): KVM, Xen, VMware, Hyper-V (portable generally on same hypervisor)
  + containers (container engine): podman, orchestration tools: RHOCP, Kubernetes (portable on OCI-compliant engine)
+ Multi-container Applications: distributed across several containers (compose-spec), include ephemeral/persistent containers to supply storage, networking, etc.
+ Kubernetes: containers orchestration service (deployment, management, scaling, high uptime, fault tolerance)
  + manages pools of resources (CPU, RAM, Storage, networking, horizontal scaling, self-healing, automated rollout, secrets/conf management,inter-service communication by assign DNS entries to each set of containers)
  + pod: small manageable unit (SINGLE APP with ONE to N containers and its resources) 
  + operators: kubernetes apps that update the cluster state and react to changes in application state
+ RHOCP: Red Hat OpenShift Container Platform
 + add components and services to kubernetes
   + Unified UI/remote management
   + load balancing simplified
   + multitenancy
   + increased security 
   + routes: easily services routes exposition
   + monitoring/auditing (advanced metrics/logging)
   + lifecycle app management (developer workflow: CI/CD pipelines, Source-to-Image(S2I - containers images from source)
    1. pod definition
    2. pod assignation to a healthy cluster node
    3. pods running until containers finish
    4. pods & containers removing/retained to logs review	

