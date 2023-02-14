# Helm Lab 2

1- create python chart (including deployment+svc+configmaps+ingress)

``` helm create pythonapp ```

then
we customize/recreate out template and add to it the configMap.yaml file

then

```helm install mypython ./pythonapp```

2- create redis chart (include deployment+svc+configmaps)

```helm create redis```

then
we customize/recreate out template and add to it the configMap.yaml file

then

```helm install redisexten1 ./redis```

## output

```bash
controlplane $ k get all
NAME                                      READY   STATUS    RESTARTS   AGE
pod/mypython-pythonapp-6688fc4b9b-8qr92   1/1     Running   0          41m
pod/mypython-pythonapp-6688fc4b9b-fx76j   1/1     Running   0          41m
pod/redisexten1-556b77fcf6-5ktsl          1/1     Running   0          43m

NAME                         TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
service/kubernetes           ClusterIP   10.96.0.1       <none>        443/TCP          19d
service/mypython-pythonapp   NodePort    10.102.27.36    <none>        8000:30163/TCP   41m
service/redisexten1          ClusterIP   10.103.173.16   <none>        6379/TCP         43m

NAME                                 READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/mypython-pythonapp   2/2     2            2           41m
deployment.apps/redisexten1          1/1     1            1           43m

NAME                                            DESIRED   CURRENT   READY   AGE
replicaset.apps/mypython-pythonapp-6688fc4b9b   2         2         2       41m
replicaset.apps/redisexten1-556b77fcf6          1         1         1       43m
controlplane $ k get cm
NAME               DATA   AGE
kube-root-ca.crt   1      19d
python-env         6      41m
```
