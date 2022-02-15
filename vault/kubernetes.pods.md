---
id: xS4a2VvW7vHG500rq8Ae0
title: Deploying Kubernetes Pods
desc: 'Deploying pods onto Kubernetes clusters.'
updated: 1644946767836
created: 1644876750896
stub: false
---

In order to deploy a Kubernetes Pod with a YAML file, use the template below and customize it to your specific needs.

```yml
apiVersion: v1
kind: Pod
metadata:
  name: podder
  labels:
    name: nginx-test
    color: orange
    meat: bacon
spec:
  containers:
  - name: webserver
    image: nginx
```