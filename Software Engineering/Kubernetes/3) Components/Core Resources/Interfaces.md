The three core interfaces to kubernetes is CRI, CNI, and CSI. Despite being a massive program, most of Kubernetes actually follows a fairly straight forward runtime architecture. 
## Container Runtime Interface (CRI)
This is how the kubelet asks for a runtime environment to begin pulling and running containers. In this case, you would use the containerd CRI. If you swap the runtime underneath, it doesnt matter because the API remains the same 
## Container Network Interface (CNI)
This is how pods get ip addresses, and paths to every other pod. This is what fundamentally ensures traffic to and from each pod is routed correctly. Again, as long as the API remains the same, you can swap out any and all different network interfaces and the runtime behaviour remains the same.
## Container Storage Interface (CSI)
How external storage gets provisioned and mounted into pods. It is the storage plugin point to allocate and distribute storage across the cluster.
## CoreDNS
This ensures there is a DNS that comes standard describing all the microservices inside a cluster. This ensures that you dont need to "bootstrap" a DNS on your cluster for when youre just starting out.
