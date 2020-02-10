

# Helloworld service (istio Fault Injection example)

We will distribute load with fault injection within the scope of istio-example

This sample includes two versions(v1,v2,v4) of a simple helloworld service that returns its project version when called. It can be used as a test service when experimenting with version routing.

This service is also used to demonstrate  fault injection deployments working in conjunction. See fault injection deployments using Istio. Code repo for image [github\dotnet-example](https://github.com/OktaySavdi/dotnet-example)

## Start the helloworld service

The following commands assume you have [automatic sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#automatic-sidecar-injection) enabled in your cluster. If not, you'll need to modify them to include [manual sidecar injection](https://istio.io/docs/setup/additional-setup/sidecar-injection/#manual-sidecar-injection).

I used that command

    kubectl label namespace helloworld istio-injection=enabled

Deploying version v1, v2, v4 or both:

    kubectl create -f FaultInjection_Example/
    
![https://github.com/OktaySavdi/istio-example/tree/master/FaultInjection_Example](https://user-images.githubusercontent.com/3519706/74103391-c147bd00-4b5c-11ea-8394-3e3a8717594f.png)



## Generate load

    while true; do curl -s "http://[NodeIP]:[IstioIngressNodeport]/"; sleep 0.5; echo -e '\n'; done
    
    while true; do curl -s "http://10.10.10.10:30292/"; sleep 0.5; echo -e '\n'; done 

## Monitoring and Control

Control istio Config

![https://github.com/OktaySavdi/istio-example/tree/master/FaultInjection_Example](https://user-images.githubusercontent.com/3519706/73649385-b985a580-4690-11ea-8065-835446113ac8.png)

**Control Graph**

![https://github.com/OktaySavdi/istio-example/tree/master/FaultInjection_Example](https://user-images.githubusercontent.com/3519706/74160238-261f1800-4c2e-11ea-80cd-7f8a10d6ef3d.png)

**Overview Console**

![https://github.com/OktaySavdi/istio-example/tree/master/FaultInjection_Example](https://user-images.githubusercontent.com/3519706/73649574-1f722d00-4691-11ea-8f8f-f9ce8f21b4fa.png)

**Inbound Metrics**

![https://github.com/OktaySavdi/istio-example/tree/master/FaultInjection_Example](https://user-images.githubusercontent.com/3519706/73649621-3d3f9200-4691-11ea-9a4f-d12737d9c59a.png)

**CLI on Server**

![https://github.com/OktaySavdi/istio-example/tree/master/FaultInjection_Example](https://user-images.githubusercontent.com/3519706/74160371-58c91080-4c2e-11ea-869c-4bcb6ab56479.png)