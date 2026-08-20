# Podman *run*
To run a container, just enter the command `podman run`
### Flags:

| Flag   | Usage                                                                                                                                                                                                                                                             |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **-d** | 'detached': meaning you want to run the container detached from the current ongoing terminal, and then will run in the background                                                                                                                                 |
| **-t** | Specifies that, if necessary, you would like to be able to open a virtual terminal into the container                                                                                                                                                             |
| **-p** | Specifies a port forward. This means users will use the first port for external tcp access, and then the 2nd port is where that will be forwarded to inside the terminal. For example 8080/80 is port 8080 outside the terminal, and then 80 inside the terminal. |
|        |                                                                                                                                                                                                                                                                   |
# Podman *stop* and *rm*
`podman stop` is used to stop an already running container, and `podman rm` is used to remove a container (note, containers still exist even after they are stopped)
### Flags

| **Flag** | **Usage**                                                                                     |
| -------- | --------------------------------------------------------------------------------------------- |
| **-l**   | for "latest", denoting that you want to stop whatever the most recently created container was |
# Podman *ps*
`ps` is used to list all running containers, with command: `podman ps`
### Flags

| **Flag** | **Usage**                                                                                                                                                  |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **-a**   | for "all", denoting that you want to see all containers on the host, including containers that have exited (no `-a` means you only see running containers) |
# Podman *top*
`top` is used to list all the running processes across all containers running
### Flags

| **Flag** | **Usage**                                                                                             |
| -------- | ----------------------------------------------------------------------------------------------------- |
| **-l**   | for "latest", denoting that you want to see the information regarding the latest container(s) created |
# Podman *images*
`podman images` is used to list all images available on the machine