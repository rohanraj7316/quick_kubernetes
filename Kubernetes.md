## Intro To Kubernetes
portable, extensible, open-source platform for managing containerized workloads and services,
that facilitates both declarative configuration and automation.

## Deployment Generation
* Nomadic era
* VM era
* Container era

**Deployment History**

![Deployment History](https://github.com/rohanraj7316/quick_kubernetes/blob/master/images/deployment.png)

## Components

* **Pods**
    * It's a group of one or more containers.
    * Pods are ephemeral, with a limited lifespan. When scaling back down  or upgrading to a new version, for instance, pods eventually die.
    * Pods are responsible for horizontal autoscaling.
    * Help in performing rolling updates.
    * Types of Pods:
        1. ReplicaSet - It ensures the specified number of pods are running.
        2. Deployment - is a declarative way of managing pods via ReplicaSets. Includes rollback and rolling update mechanisms.
        3. Daemonset - ensuring that each node run an instance of a pod. Used for cluster services, like health monitoring and log forwarding.
        4. StatefulSet - is tailored to managing pods that must persist or maintain state.
        5. Job and CronJob - run short-lived jobs as a one-off or on a schedule.
    * Architecture ![pod](https://github.com/rohanraj7316/quick_kubernetes/blob/master/images/pod.png)

* **Services**
    * Kubernetes way of configuring a proxy to forward traffic to a set of pods.
    * Instead of static IP address-based assignments, Services use selectors (or labels) to define which pods uses which service.
    * By default, services are only reachable inside the cluster using the clusterIP service type. Other service types do allow external access.
    * LoadBalancer type is the most common in cloud deployments. It will spin up a load balancer per service on the cloud environment,
    which can be expensive.
    * **Ingress** - a high-level abstraction governing how external users access services running in a Kubernetes cluster using host- or URL-based HTTP routing rules. allow you to expose multiple services under the same IP address, using the same load balancers.
    * Architecture ![services](https://github.com/rohanraj7316/quick_kubernetes/blob/master/images/services.png)

* **Networking**
    * Kubernetes has a distinctive networking model for cluster-wide, podto-pod networking. it's called Container Network Interface (CNI).
    * Containers inside pods can communicate without any restrictions (exists between same namespace and same IP). can communicate using localhost
    * Pods can communicate with each other using the pod IP address, which is reachable across the cluster.
    * Moving from pods to services, or from external sources to services, requires going through kube-proxy.

* **Cluster Nodes** 
    * Worker machines that runs pods.
    * Managed by master nodes.
    * Kubelet - primary and most important controller.
    * Drives container execution layer.
    * Architecture ![nodes](https://github.com/rohanraj7316/quick_kubernetes/blob/master/images/cluster.png)

* **Control Plane**
    * Maintains a record of all Kubernetes objects. It helps in managing object states, responding to changes in the cluster; it also works to make the actual state of system objects match the desired state.
    *  Made up of three major components:
        1. kube-apiserver - API server for front end. kube-apiserver is designed to scale horizontally that is,
        it scales by deploying more instances. You can run several instances of kube-apiserver and balance traffic
        between those instances.
        2. kube-controller-manager - it watches the shared state of the cluster through api-server and update it's state to desired state.
        all controller have it's own state. but to reduce complexity it's been compiled into one and run as separate processes. controller 
        includes following processes:
            * Node controller
            * Replication controller
            * Endpoints controller
            * Service Account & Token controllers
        3. kube-scheduler - Watches for newly created Pods with no assigned node, and selects a node for them to run on.
        Factors taken into account for scheduling decisions include: individual and collective resource requirements, hardware/software/policy constraints, data locality, inter-workload interference, and deadlines.
    * Architecture ![control_plane](https://github.com/rohanraj7316/quick_kubernetes/blob/master/images/control_plane.png)

* **Cluster Architecture**
    * From a high level, a Kubernetes environment consists of a control plane (master), a distributed storage system for keeping the cluster state consistent (etcd - high available key value storage used for backing up cluster state variables), and a number of cluster nodes (Kubelets - service runs inside each node responsible for managing pods/containers too.).
    * Architecture ![cluster](https://github.com/rohanraj7316/quick_kubernetes/blob/master/images/cluster.png)
