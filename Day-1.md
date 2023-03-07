## Set up Auto-completion


1- Kubectl autocomplete in bash in the current shell. Bash completion package


* < : Gives input to a command.
* source :  reads and executes the file content in the current shell.
* `kubectl completion bash`: kubectl completion script source 

Check if bash-completion is already installed:

`type _init_completion`

`apt-get install bash-completion`


```
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bashrc
```

## Aliases



```
alias k="kubectl"
alias kn="kubectl get nodes -o wide"
alias kp="kubectl get pods -o wide"
alias kd="kubectl get deployment -o wide"
alias ks="kubectl get svc -o wide"

Describe K8S resources

alias kdp="kubectl describe pod"
alias kdd="kubectl describe deployment"
alias kds="kubectl describe service"
alias kdn="kubectl describe node"
```


```
export do="--dry-run=client -oyaml"
```

```
k run simple-pod nginx --image=nginx $do  
k run simple-pod nginx --image=busybox --command sleep 3600 $do
```

## Short form of commands


|Long  | Short |
| ------------- | ------------- |
|componentstatuses|cs|
|configmaps|cm
|endpoints|ep|
|events|ev
|limitranges|limits|
|namespaces|ns|
|nodes|no|
|persistentvolumeclaims|pvc|
|persistentvolumes|pv|
|pods|po|
|replicationcontrollers|rc|
|resourcequotas|quota|
|serviceaccounts|sa|
|services|svc|
|customresourcedefinitions|crd, crds|
|daemonsets|ds|
|deployments|deploy|
|replicasets|rs|
|statefulsets|sts|
|horizontalpodautoscalers|hpa|
|cronjobs|cj|
|certificiaterequests|cr, crs|
|certificates|cert, certs|
|certificatesigningrequests|csr|
|ingresses|ing|
|networkpolicies|netpol|
|podsecuritypolicies|psp|
|replicasets|rs|
|scheduledscalers|ss|
|priorityclasses|pc|
|storageclasses|sc|

## ref

https://unix.stackexchange.com/questions/159513/what-are-the-shells-control-and-redirection-operators
