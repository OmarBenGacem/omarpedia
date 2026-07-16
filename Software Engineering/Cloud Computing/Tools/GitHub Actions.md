[[Software Engineering/Kubernetes/5) Deployment/CICD/CICD|CICD]] [[Software Engineering/Kubernetes/5) Deployment/5) Deployment|Deployment]] [[Software Engineering/Kubernetes/Kubernetes|Kubernetes]]
#CICD #Kubernetes #Deployment
## Functionality
Github actions is a CICD service run by github, that can execute key CICD steps in a simple, free to use, format. It is a *.yaml* file, split into a **name** block which is the name that shows up on github, the **on** block that describes the trigger, the **jobs** block, which specifies a job, and then the **steps** block that specifies what steps to do on a run.
# Setup
To setup a github actions workflow, you need to create a *.github* folder that has a subfolder titled *workflows*. github will automatically search this directory for *yaml* files that exist in this directory and use them as a workflow.
# Usage
## *Name* Block
## *on* Block
The on block describes the triggers that should cause a build. Below is an example of a very common configuration, that gives the instruction to build either when manually triggered (*workflow_dispatch*) or when someone pushes to the main branch.

![[_attachments/Screenshot 2026-07-13 at 4.50.11 PM.png|317]]
## *jobs* Block
The jobs bock outlines steps that are executed on a virtual machine to build the code. The argument *runs-on* is used to specify what the VM is, and note that there are other 'quality of life' arguments available such as name, description (not shown), and id that helps you debug your cicd pipeline, and ensure on github everything looks as it should.

![[_attachments/Screenshot 2026-07-13 at 4.54.14 PM.png|521]]

The first step is a checkout, which is a pre-written command by github. This one is very common, and it just tells it to checkout the repository and check everything is in order.

Note that words like 'Fetch' and 'Setup' (not shown) and 'Checkout' are arguments for pre-written tasks that can be done to save a lot of time. However the *run* lines are running specific commands that need to be directly specified by the user, should a task not fall within the available commands.