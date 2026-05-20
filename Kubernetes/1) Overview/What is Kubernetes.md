## Objective Use Case

The use case for Kubernetes is to deploy a persistent, scalable, and highly available service for clients across a network. An example of software products that use Kubernetes are Netflix, Pokémon Go, and Thales’s Vantis Federal Radar Data Enclave (VFRDE). As seen in these examples, these are products that needs to be persistent (videos always available on Netflix), scalable (many users for Pokémon Go), and highly available (always need to be logging data). These are all production software’s that use Kubernetes for their operation, and note they all meet these criteria. Some bad examples of projects using Kubernetes would be a locally run video game, a static webpage, or a not-web-based code IDE.

## High Level Overview

### One Sentence Summary

Kubernetes is the background software that enables containerized applications to run persistently, and integrate with other containerized applications to provide a service.

### Many Sentence Summary

#### High Level

Once set up[^1], the purpose of Kubernetes is to allow for all the “background tasks” to take care of themselves. These include restarting crashed pods resource management, DNS management, I/O networking, database integration ect … such that all that actually needs to be managed is the operation of each pod, as well as other high level design decisions.

For example, suppose there is one computer with 10 CPU cores and 10 GB of memory, and 3 pods running on it. You could run around and allocate the compute between the pods. But the purpose of Kubernetes is to have it do it for you, it dynamically scales the resources to each pods so they can all run safely. Another example is imagine the pods need to talk to each other via an IP address, Kubernetes can do this for you (discussed in **Error! Reference source not found.**) to make it much easier to do it for you.

#### Availability

Kubernetes guarantees a very high degree of availability for the services it facilitates. If you run code on your laptop and then close the laptop, it stops. Kubernetes lets you r

#### Scalability

Take the Netflix case, all users in Netflix should experience identical user experiences, but should not have to “share” a page with another user. Similarly, when a new user joins in, Netflix wants to “replicate” their services for the new user. Kubernetes is very good at doing this, and this is one of it’s advantages, all you need to do is to tell it to reproduce itself for all new users, you don’t need to do it.

#### Persistency

Kubernetes runs continually and has very good error correcting protocols to ensure that even if Kubernetes crashes, it can keep going as well as troubleshoot itself.

  

---

[^1]: This is the biggest pain in the ass ever, good luck chief