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


```
alias k=kubectl

complete -o default -F __start_kubectl k
``



## ref

https://unix.stackexchange.com/questions/159513/what-are-the-shells-control-and-redirection-operators
