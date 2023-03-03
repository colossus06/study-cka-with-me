# study-cka-with-me
study-cka-with-me



* Processing YAML Content-yq


 * Parsing with jq
 
 
* View JSON output in readable format: `kubectl get pods -o json | jq '.'`
* Read the first element `kubectl get pods -o json | jq 'first(.[])'`
