This is a default cluster management webpage that is available for your clusters that is build into the software. You need to turn it on via `kubectl apply [dashboard-yaml-uri]`, and then enable it. Here is the commands and steps that you need to deploy it 

## `kubectl apply [dashboard-yaml-uri]`
note that the URI will be a web link to pull it straight from github (hint hint). This means there is no need to download, you just get it and go. This first step installs the dashboard itsself, it will create the namespace, deployment, service and roles. This actually creates the dashboard
## `kubectl apply -f dashboard.adminuser.yml`
This next step, from the local machine, creates the service account and a ClusterRoleBinding and a ServiceAccount ([Roles]). This actually gives you something to log into the dashboard. This is the 'setup phase' whereas the first step was the 'install phase'. 
## `kubectl create token admin-user -n kube-system`
You need to get a token to login to the dahsboard. This gives you a token (better auth later)
## `kubectl proxy`
After running it, you should see that a URL was created for port 8001. This menas that you can actually access the dashboard. After pasting the token, you should see an empty dashboard (until you put some pods on it)!!
# Authentication Setup
## Cleanup and Usage