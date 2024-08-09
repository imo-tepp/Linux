# Virutalization

Virtualization is technology that you use to create a virtual representations of servers, storage, networks and other physical machines. It mimics the functions of physical hardware to run multiple virtual machines simultaneously on a single physical machine.

There are several software that can be used for virtualisation:
- *VMware* can partition a single physical server into multple virtual servers. It works with Linux and can be used concurrently on the same hardware.
- *Virtual Box* is a free virtualization software that can be used to run virtual machines with different operating system on your computer.
- *QEMU* is an emulator and a virutalization program that can run programs and operating system for a specific CPU on a different machine.
- *Citrix XenServer* and *Parallels Virtuozzo Containers* are other examples of software that delivers similar experience as the ones mentioned above.

## Advantages of Virtualization
- Cost-effective: By hosting several virtual machine on a single hardware, it effectively reduce the need to purchase more hardware for computing resources.
- Better utlilzation of resources: can utlilise all the available computing resource on the hardware by virutalising it.
- Reduced Management: can manage all the virutal server through the user of a single central dashboard.
- Flexible - virtualization can run different operating system and software on the same physical machine.

## Points to Remember
- Hardware is the solution for full virtualizaion 
- VMware ESXi is an example of server operating system.
- XML standard describes the interface of web services. 
- Abstraction (simplification) enables the key benefit of cloud computing , simplified, shared and ubqiuitous access.
- Virtualization assigns a logical name for a physical resource and then provides a pointer to that physical resource when a request is made
- Several important cloud computing approaches use a strictly hardware-based approach to abstraction.
- Most data center environments experience changes to performance requirements and workload activity over time.
- All of these methods proivde users with the ability to service their own requests with minimal IT oversight
```
create a library of virtual machine templates and copy them to create new VMs
Invest in self-service virtualization provisioning systems
Give developers and testers permissions to create and deploy new VMs
Define standardized configurations for test environment virtual machines
```
- One of the primary benefits of virtualization is the ability to save the state of a VM and then move or copy it to another location.
- VMs must be able to communicate with each other, they will require network access.
- Presentation virtualization involves installing and running applications on a central server and allowing clients to access the VMs over the network. An example is the Microsofts's Windows Terminal Services
- Microsoft Hyper -V requires 64-bit CPUs with virtualization extensions, NX support, and runs only on x64 editions of Windows Server 2008.
- The initial version of Microsoft Hyper -V didn't support automatic, live migration of virtual machines or their save state to another server.
- By default, the Hyper -V Server Role isn't enabled on new installations of Window Server 2008
- Load balancing helps distributes service request to resources.
- A cloud has multiple applications instances and directs requests to an instance based on conditions.
- Computers can be partitioned into a set of virutal machines with each machine being assigned a workload systems can be virtualized through load-balancing technologies.
- Apache mod_proxy_balancer software can be used to implement load balancing.
- Load balancing can be used to increase utilization and throughput, lower latency, reduce response time and avoid system overload.
- Connections through intelligent switches, DNS, Storage resources are the network resources can be load balanced.
- Load balancing provides the necessary redundancy to make an intrinsically unreliable system reliable through managed redirection workload managers is a more sophisticated load balancer.
- They determine the current utilization of the resources in their pool.
- ADC is a combination load balancer and application server that is a server placed between a firewall or router.
- An Application Delivery Controller is assigned a virtual IP address(VIP) that maps to a pool of servers based on application specific criteria.
- Hypervisor control memory and processor resources while virtual machines control their own network and storage resources.
- Type 2 hypervisor runs on top of an operating system to provide resources to the virtual machines.