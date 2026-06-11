A container is a standalone unit of software that packages code, and all associated dependancies, allowing for it to be 'shipped' to a new host VM or machine to be run. Once shipped, these are known as 'container images', then only when they are ready to run (or 'execute'), are they actually built and then run.

Included in a container is the application code (inc scripts, software binaries, and source code), the specific runtime (such as Python or NodeJS), and all libraries, tools, configurations and dependancies. Notably, container do **not** include underlying OS services such as a kernel, hardware drivers, or storage, as it uses the host to provide these resources. 

Containers are so lightweight partially because they share their hosts operating system, and their kernel. Only the
![[_attachments/container.png]]

Containers are known as 'ephemeral[^1]', meaning that they are designed (and thus constructed) to do a specific task, and a specific task only, and once it's task is complete, it is destroyed, and then replacing it when it is done with its task. Note this also means containers do not have any kind of persistent storage. When the container is build-run-deleted-rebuilt, nothing in the 'run' phase is preserved, it starts back up from the beginning.




[^1]: Ephemeral: an adjective describing something that lasts for a very short time