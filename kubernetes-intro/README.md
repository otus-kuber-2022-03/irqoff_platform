# В процессе сделано:
 - Познакомился с тем как стартуют static pods и deployment при уделении:
```
kubectl get deployments.apps -A
NAMESPACE     NAME      READY   UP-TO-DATE   AVAILABLE   AGE
kube-system   coredns   1/1     1            1           27h

static pod and kubelet start it:
docker@minikube:/etc$ ls /etc/kubernetes/manifests
etcd.yaml  kube-apiserver.yaml  kube-controller-manager.yaml  kube-scheduler.yaml
```
 - Создал Dockerfile web/Dockerfile
 - Создал манифесты web-pod.yaml и frontend-pod-healthy.yaml

# Как запустить проект:
 - `kubectl apply -f frontend-pod-healthy.yaml`
 - `kubectl apply -f web-pod.yaml`

# Как проверить работоспособность:
 - Перейти по ссылке http://localhost:8080/index.html
 - Выполнить:
```
kubectl get pods frontend
NAME       READY   STATUS    RESTARTS   AGE
frontend   1/1     Running   0          5m43s
```
