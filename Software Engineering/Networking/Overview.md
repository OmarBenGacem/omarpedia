Networking is the process by which devices on a network are able to communicate over a single, unified standard. The networking stack is thought of as "layers", with each layer identifying the roles of "things" in that layer, and what services they provide. This allows things to abstract out the layers above, and the layers below, encouraging them to only focus on their role in the stack. There are 7 layers in networking. **It is easiest to read this bottom to top.**
# OSI Model
## 7) Application Layer
This payer provides the interfaces (apis) for your actual apps to use a network. it abstracts out everything below this so that a single app can use the network stack and only need to "think" about what the other app will see on the other side of the communication session. Examples of this are DNS, HTTP, FTP (file transfer), etc ...
## 6) Presentation Layer
This prepares the data to be sent to the application layer, it handles things like compression, encryption, etc ... 
## 5) Session Layer
This handles the creation, management, and closing of sessions. This layer is only super relevant during the very beginning and very end of a network session.
## 4) Transport Layer
This layer is where we specify the means of communication across the network. So for example here is where UDP/TCP is determined, if the connection type is a websocket, etc ... This layer focuses more on the means of communication rather than the communication itsself
## 3) Network Layer
This is the one where packets are routed through IP addresses. This "bundles" information from the data link layer and gives a remove (not necessary) address for that package to be sent off to
## 2) Data Link Layer
This routes the data between physical devices on it's own network. So this would be like a switch sending ethernet signals around to MAC addresses. This uses physical devices to route the signals from the physical layer to their destination.
## 1) Physical Layer
The physical layer is the physical (or wireless) infrastructure that allows for networking to occur. The most important role of this layer is to **transport data as bits and signals**. This facilitates the fundamental operation of networking to occur.
# TCP/IP Model 
## 4) Application
This model combines 5/6/7 all into one layer given (as you can see), they have a lot of overlap
## 3) Transport
Same as above
## 2) Network
Same as above
## 1) Data Link
A combination of layers 1 and 2.

