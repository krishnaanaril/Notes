## Docker Networking

* The three pillars of Docker networking.
    1. Container Network Model (CNM) - Master Plan/Grand design
    2. Lib Network - De facto implementation of the CNM
    3. Drivers - Network specific details
* CNM vs CNI (Container Network Interfaces). 
* CNI is more suitable for k8s.
* Single Host Networking  - Bridge networks in docker
* Multi Host Networking  - Overlay networks in docker
* MACVLAN is used to provide ip address and mac address for containers in the same network.
* MACVLAN requires network card to be configured in **promiscuous** mode. Most public cloud providers dont' allow it.
* IPVLAN is similar to MACVLAN, but doesnt' require promiscuous mode and do not get mac address for every container. 
* Http Routing Mesh (HRM) allows multiple services to listen to the same port.