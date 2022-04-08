# В процессе сделано:

Научился создавать pvc, pv, statefulset:
```
kubectl get all
NAME          READY   STATUS    RESTARTS   AGE
pod/minio-0   1/1     Running   0          33m

NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP    80m
service/minio        ClusterIP   None         <none>        9000/TCP   40m

NAME                     READY   AGE
statefulset.apps/minio   1/1     42m
 kubectl get pvc
NAME           STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
data-minio-0   Bound    pvc-30f8313a-4c18-493e-84b5-a66d4b240531   10Gi       RWO            standard       43m
 kubectl get pv
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                  STORAGECLASS   REASON   AGE
pvc-30f8313a-4c18-493e-84b5-a66d4b240531   10Gi       RWO            Delete           Bound    default/data-minio-0   standard                43m
```

Задание со звездочкой:
```
/ # env | grep MINIO_.*_KEY
MINIO_ACCESS_KEY_FILE=access_key
MINIO_ACCESS_KEY=anMacantAvacpybnicGalt
MINIO_SECRET_KEY_FILE=secret_key
MINIO_SECRET_KEY=AccugpitdeocFairlachto
```