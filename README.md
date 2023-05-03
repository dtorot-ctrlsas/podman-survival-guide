# Podman Survival Guide
Podman survival guide notes

## NOTES AND CONCEPTS
+ Containers use namespaces(isolate processes) and cgroups(resource management: CPU time allocation, memory) kernel features
+ From the OCI (Open Container Initiative) there is an application specification
+ **Container Images:** immutable data that defines an app and its libraries (_img-spec_)
+ **Container Instances:** created from container images, the executable version (include network,disks,etc runtime necessities)(_runtime-spec_)
+ **Software management**
  - **virtual machines (hypervisors)**: KVM, Xen, VMware, Hyper-V (portable generally on same hypervisor)
  - **containers (container engine)**: podman, orchestration tools: RHOCP, Kubernetes (portable on OCI-compliant engine)
+ **Multi-container Applications:** distributed across several containers (_compose-spec_), include ephemeral/persistent containers to supply storage, networking, etc.
+ **Kubernetes:** containers orchestration service (deployment, management, scaling, high uptime, fault tolerance)
  - manages pools of resources (CPU, RAM, Storage, networking, horizontal scaling, self-healing, automated rollout, secrets/conf management, inter-service communication by assign DNS entries to each set of containers)
  - **pod:** small manageable unit (SINGLE APP with ONE to N containers and its resources) 
  - **operators:** kubernetes apps that update the cluster state and react to changes in application state
+ **RHOCP:** Red Hat OpenShift Container Platform
  - add components and services to kubernetes
    - Unified UI/remote management
    - load balancing simplified
    - multitenancy
    - increased security 
    - routes: easily services routes exposition
    - monitoring/auditing (advanced metrics/logging)
    - lifecycle app management (developer workflow: CI/CD pipelines, Source-to-Image(S2I - containers images from source)
      1. pod definition
      2. pod assignation to a healthy cluster node
      3. pods running until containers finish
      4. pods & containers removing/retained to logs review	

## COMMAND REF
+ `podman -v`: podman version
+ `podman pull registry.image.io/path/name:version.release`: pull container image
+ `podman images`: list local stored podman images
+ `podman run registry.image.io/path/localImage/name:version` echo 'COMMAND': run local container and print the COMMAND output (if we run a container that is not stored locally, podman tries automatically to pull that image)
+ `podman ps`: print the local running containers
+ `podman ps --all`: print containers (running and stopped, show the UUID of the containers)
+ `podman run --rm regitry.images.io/path/name:version echo 'COMMAND'`: run and remove a container when it exits
+ `podman run --name podman_mycontainer registry.images.io/path/name/version`: the container will be named podman_mycontainer
+ `podman ps --all --format=json`: print info in json format
+ `podman run -p 8080:8080 registry.images.io/path/name:version`: expose the container with LocalPort:ContainerPort
+ `podman run -d -p 8080:8080 registry.images.io/path/name:version`: expose the container with LocalPort:ContainerPort and run in background
+ `podman run -e ENV_VAR=Value registry.images.io/path/name:version command PARAMETER`: output the command but the container use de ENV_VAR=Value
