# В процессе сделано:

ps в livenessProbe не имеет смысла:
 * если мы проверяем init пороцесс
 * нужно поправить саму command:
```
ps aux| grep [m]y_web_server_process
```
kill main process
```

Логи MetalLB:
---
{"caller":"level.go:63","event":"ipAllocated","ip":["172.17.255.1"],"level":"info","msg":"IP address assigned by controller","service":"metallb-system/web-svc-lb","ts":"2022-04-06T15:59:29.106814189Z"}
{"caller":"level.go:63","event":"serviceUpdated","level":"info","msg":"updated service object","service":"metallb-system/web-svc-lb","ts":"2022-04-06T15:59:29.158990004Z"}
```
и curl:
```
$ curl http://10.97.55.94/web/ -s |& head -2
<html>
<head/>
```

## DNS через MetalLB

С хостовой системы:
```
dig +short kubernetes.default.svc.cluster.local @172.17.255.10
10.96.0.1
```

## Ingress для Dashboard
```
$ curl https://d.local:443/dashboard  -sk |& head
Copyright 2017 The Kubernetes Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
```

## Ingress для Dashboard:
```
$ curl http://10.97.55.94/web/index.html -s | grep web
export HOSTNAME='web-canary-5767868c9-llzlg'
172.17.0.12     web-canary-5767868c9-llzlg</pre>
$ curl http://10.97.55.94/web/index.html -s | grep web
export HOSTNAME='web-6765988c5c-tb5c7'
172.17.0.3      web-6765988c5c-tb5c7</pre>
$ curl http://10.97.55.94/web/index.html -s | grep web
export HOSTNAME='web-6765988c5c-8cdlb'
172.17.0.4      web-6765988c5c-8cdlb</pre>
$ curl http://10.97.55.94/web/index.html -s | grep web
export HOSTNAME='web-6765988c5c-wgrp5'
172.17.0.5      web-6765988c5c-wgrp5</pre>
$ curl http://10.97.55.94/web/index.html -s | grep web
export HOSTNAME='web-6765988c5c-tb5c7'
172.17.0.3      web-6765988c5c-tb5c7</pre>
$ curl http://10.97.55.94/web/index.html -s | grep web
export HOSTNAME='web-canary-5767868c9-7zlxb'
172.17.0.7      web-canary-5767868c9-7zlxb</pre>
```