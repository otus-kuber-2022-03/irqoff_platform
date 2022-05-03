# В процессе сделано:

## Helm

```
helm version
version.BuildInfo{Version:"v3.8.1", GitCommit:"5cb9af4b1b271d11d7a97a71df3ac337dd94ad37", GitTreeState:"clean", GoVersion:"go1.17.8"}
```

Установил chartmuseum:
```
helm upgrade --install chartmuseum stable/chartmuseum --wait  --namespace=chartmuseum --version=2.14.2  -f kubernetes-templating/chartmuseum/values.yaml
```

Установил harbot:
```
helm upgrade --install harbor  harbor/harbor --version=1.9.0 --namespace harbor --create-namespace -f kubernetes-templating/harbor/values.yml
```

## kubecfg

```
kubecfg version: v0.26.0
jsonnet version: v0.18.0
client-go version: v0.0.0-master+$Format:%H$
```

Установил hipster-shop:
```
kubecfg update services.jsonnet --namespace hipster-shop
INFO  Validating deployments paymentservice
INFO  validate object "apps/v1, Kind=Deployment"
INFO  Validating services paymentservice
INFO  validate object "/v1, Kind=Service"
INFO  Validating deployments shippingservice
INFO  validate object "apps/v1, Kind=Deployment"
INFO  Validating services shippingservice
INFO  validate object "/v1, Kind=Service"
INFO  Fetching schemas for 4 resources
INFO  Creating services paymentservice
INFO  Creating services shippingservice
INFO  Creating deployments paymentservice
INFO  Creating deployments shippingservice
```

## kustomize

Установил cartservice:
```
kubectl apply -k kubernetes-templating/kustomize/overrides/stage/
service/stage-cartservice created
deployment.apps/stage-cartservice created
```