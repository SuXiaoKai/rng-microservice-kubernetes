# RNG microservice Kubernetes files

### Quick Get-it-up-n-running deployment example


**TL;DR** :

`$ kubectl apply -f rng-deploy.yml`

`$ kubectl apply -f rng-service.yml`

<pre>
[nodeMaster ~]$ kubectl apply -f rng-deploy.yml
deployment "random-gen" created

[nodeMaster ~]$ kubectl apply -f rng-service.yml
service "rnd-svc" created

[nodeMaster ~]$ kubectl get pods
NAME                         READY     STATUS    RESTARTS   AGE
random-gen-c54fbb57b-8v96p   1/1       Running   0          1m
random-gen-c54fbb57b-gb8gf   1/1       Running   0          1m
random-gen-c54fbb57b-n7gwt   1/1       Running   0          1m
random-gen-c54fbb57b-zcg6v   1/1       Running   0          1m

[nodeMaster ~]$ kubectl get services
NAME         TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
...
rnd-svc      NodePort    10.111.168.84   none        3000:31361/TCP   25s

[nodeMaster ~]$ kubectl get deployments
NAME         DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
random-gen   4         4         4            4           1m



[nodeMaster ~]$ curl 10.111.168.84:3000
{
 "entropy":3973,
 "msg":"done",
 "passwd":"2tos#@1usu-sJs31Y#myb",
 "rnd":"f8c2c41f67dcb5a7e90b...a6d8d44e19ff572f16",
 "rndnum":"11093377823535699098408057...86386463"
 }


[nodeMaster ~]$ curl 10.111.168.84:3000?passwd=1
7prvwieA+Am9q=7obQL%Ny

</pre>
