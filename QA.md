
## Q1
* Create a new pod called super-user-pod with image busybox:1.28. 
* Allow the pod to be able to set **system_time**.
* The container should sleep for 4800 seconds

<details><summary>Answer</summary>
<p>
  
 `k run super-user-pod --image=busybox:1.28 --dry-run=client -oyaml --command sleep 4800 >super-user-pod.yml`

```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: super-user-pod
  name: super-user-pod
spec:
  containers:
  - command:
    - sleep
    - "4800"
    image: busybox:1.28
    name: super-user-pod
    securityContext:
      capabilities:
        add:
        -  "SYS_TIME"
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
 ```
` k apply -f super-user-pod.yml`

![image](https://user-images.githubusercontent.com/96833570/222956290-b88458e0-dcfa-4daa-a897-fd1c6bd2d052.png)

  </p>
</details>

## Q2
* Create a new deployment called web-proj-268, with image nginx:1.16 and 1 replica. 
* Record the version. 
* Next upgrade the deployment to version 1.17 using rolling update. 
* Make sure that the version upgrade is recorded in the resource annotation.

<details><summary>Answer</summary>
<p>

`k create deploy web-proj-268 --image=nginx:1.16`


![image](https://user-images.githubusercontent.com/96833570/222957077-c492023f-5693-4a4d-9c21-dadd4159e440.png)


`k describe deployment.apps web-proj-268`

`k describe deployment.apps web-proj-268 | grep -i image`

`k set image deployment web-proj-268 nginx=nginx:1.17 --record`

` k rollout history deployment web-proj-268`

![image](https://user-images.githubusercontent.com/96833570/222957332-1a86bc28-620e-4865-8ef3-41249967d1b4.png)

`kubectl annotate deploy web-proj-268 kubernetes.io/change-cause='version change from 1.16 to 1.17' --overwrite=true`

![image](https://user-images.githubusercontent.com/96833570/222957448-74266788-9232-4826-bef8-779fc9accb5b.png)

</p>
</details>



## useful sources

<details><summary>Code examples</summary>
<p>


* Create the deployment

`kubectl create deployment nginx --image=nginx:1.16.0 --replicas 1`

* check the history

`kubectl rollout history deployment nginx`

* update the image on deployment

`kubectl set image deployment nginx nginx=nginx:latest`

* Annotate the deployment now and create the history

`kubectl annotate deployment nginx kubernetes.io/change-cause="version change to 1.16.0 to latest" --overwrite=true`

* Check the history

`kubectl rollout history deployment nginx`

</p>
</details>
