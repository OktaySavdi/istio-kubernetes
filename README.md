# What is Istio Service Mesh?

We will distribute load with loadbalancing within the scope of istio-example

Istio service mesh provides several capabilities for traffic monitoring, access control, discovery, security, resiliency, and other useful things to a bundle of services. It delivers all that and strikingly does not require any changes to the code of any of those services.

# The Istio Service Mesh Architecture

-   Istio service mesh is an intentionally designed abstraction that has both a control plane and a data plane.
-   Istio is a service mesh created by the combined efforts of IBM, Google, and Lyft. The sidecar patterns are enabled by the Envoy proxy and are based on containers.

![https://github.com/OktaySavdi/istio-example](https://user-images.githubusercontent.com/3519706/73640623-a6b6a500-467f-11ea-8dd0-a5c69161654a.png)

**Envoy**

-   Envoy is an open-source extension and service proxy provider, built for cloud-extensive meshes. The Istio mesh creates an extendible proxy system through Envoy.

**Mixer**

-   The mixer is a part of the service mesh that helps in enforcing safety protocols, allowing access controls and implementing usage policies and works independently from the mesh.

**Pilot**

-   Pilot provides all services for the Istio Envoy sidecars and allows for a more coherent traffic management system with high level routing.

**Citadel**

-  Performs TLS certificate management

**Galley**

-  It offers configuration management services for Istio.

**Telemetry**

-  Collects statistics on machines

# Determining the ingress IP and ports

Execute the following command to determine if your Kubernetes cluster is running in an environment that supports external load balancers:

    $ kubectl get svc istio-ingressgateway -n istio-system
    NAME                   TYPE           CLUSTER-IP       EXTERNAL-IP     PORT(S)                                      AGE
    istio-ingressgateway   LoadBalancer   172.21.109.129   130.211.10.121  80:31380/TCP,443:31390/TCP,31400:31400/TCP   17h

If the **EXTERNAL-IP** value is set, your environment has an external load balancer that you can use for the ingress gateway.

If the **EXTERNAL-IP** value is <none> (or perpetually <pending>), your environment does not provide an external load balancer for the ingress gateway. In this case, **you can access the gateway using the service’s node port.**

## We did 11 examples on istio

 **1. istio canary example** 
 
 **2. istio circuit breaking example**
 
 **3. istio header example**
 
 **4. istio mirror example**
 
 **5. istio oneway example**
 
 **6. istio random example**
 
 **7. istio round robin example**
 
 **8. istio session affinity example**
 
 **9. istio timeout example**
 
 **10. istio fault injection example**
  
 **11. istio mTLS example**
