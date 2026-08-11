[[Software Engineering/Kubernetes/5) Deployment/CICD/CICD|CICD]] [[Software Engineering/Kubernetes/5) Deployment/5) Deployment|Deployment]] [[Software Engineering/Kubernetes/Kubernetes|Kubernetes]]
#CICD #Kubernetes #Deployment 

# Functionality
ArgoCD is a complete CICD package to automate the deployment and management of containers on a cloud compute server. Argo has the full toolchain all connected together such that someone can

Argo contains 3 core services for it's operation. The API Server and Repository Server act as services to allow the application controller (the app) to run. 
### API Server
Argo has an API service (gRPC/REST) to allow for the WEB UI, CLI, and all other systems to connect to Argo and perform the operations
### Repository Server
This contains a cache of the git repository as well as the manifests available. This means that they are kept constantly in sync, but without any building and/or functionality. 
### Application Controler
The 'do-er', this service allows for continual monitoring, and comparing the live state against the desired state, for both the production and the github (to keep it in sync with the repository). 
![[_attachments/Screenshot 2026-07-16 at 3.14.04 PM.png]]
### Deployments and Components
#### argocd-dex-server
This is just an embedding of Dex, which is an open source identiy service that bridges existing identity providers (google, github, etc ...) to argo's openID connect (OIDC) authentication. This is needed because argo handles authentication natively, it lets you bypass passwords (if you want) and just use your corporate login. 
#### argocd-metrics / argocd-server-metrics
ArgoCD exposes an API serer for application and server metrics for #Prometheus, this lets you further integrate things like grafana.
#### argocd-redis
Redis (REmote DIctionary Server) is used as a caching technology that works with the ArgoCD repository server 
#### argocd-repo-server
The clone of the git repository, keeping it up to date and generating manifests with the appropriate tools.
# Setup
### Predicates
You'll need access to the *kubectl* command because ArgoCD is a Kubernetes service, it doesnt really work anywhere else. You'll also need the Kubernetes cluster (and the kubeconfig) to host the Argo instance, as well as admin level access. You will also need access to the repo (github) storing the source code. As Argo works as a bridge to get source code running on a cluster, you need both of these set up in order to deploy argo.
### Availability
Argo comes in two forms, the high and low availabilities. The non high availability is super useful for test and dev environments, as they are much more lightweight, and overall simpler. It consists only of a single pod and replica to make everything a bit easier. The High availability option should really only be used on production system due to multiple pods and replicas, so that it has high availability and resiliency. Finally, there is also the core install, which omits certain services for ultra lightweighted-ness.
### Deployment Scope
In general you deploy Argo at a cluster level, and this is good if you have cluster level access. Alternatively, you can deploy at a namespace level, which ius helpful if you are only have namespace access, or if you are deploying to a different cluster from where argo is running.  
## Procedure
To begin, it is best to isolate Argo into it's own namespace so that it can be managed easier.
```
kubectl create namespace argocd
```
Now it is time to actually install argocd, and you can take it from the yaml file that is available at the github and can be cloned using the following command. Note how the *-n* flag is used to specify the argocd namespace and -f  
```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
# Usage
## CLI Overview
The Argo CLI gives direct access to the API server, and allows for (most) of the stuff you can do on the UI, as well as some CLI specific tasks. Install via your package manager of choice.
