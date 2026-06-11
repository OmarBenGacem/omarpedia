The purpose of a virtual machine is to convince local file systems (virtual machines) that they are all alone on a machine, while that filesystem is using resources that are actually a part of a larger pool of resources. These new local filesystems are called virtual machines, and the software that manages them is known as a hypervisor.

![[_attachments/Hypervisor.png|557]]

A good Hypervisor allows all VMs to independently run their own applications, as well as allowing each VM to seamlessly access the external network, while preventing processes running in their own environment from interfering with other tenants, as well as ensuring they themselves are safe from other tenants.

The only difference between a VM and a physical machine is the hardware components. A vm has it's own kernel and OS etc ..., it is literally only missing hardware.