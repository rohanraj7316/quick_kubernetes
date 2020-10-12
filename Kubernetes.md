# Intro To Kubernetes
    portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation.

## Deployment Generation
    * Nomadic era
    * VM era
    * Container era

**Deployment History**

![Deployment History](./images/deployment.png)

## Components

* **Pods And Services**
    * it's a group of one or more containers.
    * Pods are ephemeral, with a limited lifespan. When scaling back down  or upgrading to a new version, for instance, pods eventually die.
    * Pods are responsible for horizontal autoscaling.
    * Help in performing rolling updates.
    * Architecture ![Node](./images/pod.png)

* **Nodes** 
    * worker machines(At least one is needed).
    * Control Plane - manages nodes and pods(basic things).
        * kube-apiserver

        * etcd
        * kube-scheduler
        * kube-controller-manager
        * cloud-controller-manager
    * Node Components - manages each node(basic things).
        * kubelet
        * kube-proxy
        * Container runtime

**Basic Structure**

![Basic Layout](./images/layout.png)

