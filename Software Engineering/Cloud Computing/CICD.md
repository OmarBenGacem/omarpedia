Continuous Integration Continuous Delivery (CICD) is the name for a family of programs and services that are used to manage large scale software products. It's purpose is to allow for large software systems to remain functioning, while continually updating, modifying, or otherwise changing the underlying code. This means that from the perspective of the user, they experience no drops in service, and will continually see/experience new features on a rolling basis. This also allows for a very high degree of control for version control for software.

## Continuous Integration
Continuous Integration (CI) is the process of building a codebase as soon as it is pushed, and then beginning to write test cases for the codebase and run them as soon as its built. This also acts as a validation step to make sure the changes do not break anything.
## Continuous Delivery
Code can be deployed as soon as it is built and then pushed to a service to run.

![[_attachments/Screenshot 2026-07-13 at 4.23.39 PM.png|542]]
## Components
### Source Code Repository
A CICD pipeline needs to have a source code repository that acts as "the thing" that is being deployed. Note that everything being done is with respect to a full pipeline, so from code -> product. This means that there needs to be one (or many) repositories that act as such.
### Build Processes
A build process describes how to package code for production. You can't just send source code off and say "go", there needs to be a way for it to be put into a "production ready form" such as a binary or a container. This is all included in the build process, and it does all of it for you!
### Automated Tests
To check that the code operates correctly, and for other convenience reasons, it is helpful to implement test cases to know exactly what is going wrong when attempting to run a scenario.;
### Automated Deployment
Where to "put" the code once compiled, tested, and ready to go!