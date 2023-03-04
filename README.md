# study-cka-with-me
study-cka-with-me



* Processing YAML Content-yq


 * Parsing with jq
 
 
* View JSON output in readable format: `kubectl get pods -o json | jq '.'`

![image](https://user-images.githubusercontent.com/96833570/222890131-20ef709f-0d3f-411f-8e91-08ebf411dbb4.png)


`k get no -ojson | jq '.items[].kind'`


![image](https://user-images.githubusercontent.com/96833570/222890522-ae6235e7-d767-4542-82d0-4864f97ff645.png)


kubectl -n -ojson | jq '.items[] | select(.status.containerStatuses[].ready==false) | .metadata.name'

* Read the first element `kubectl get pods -o json | jq 'first(.[])'`

