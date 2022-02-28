---
id: eail1jp5vo3trpbrz3vgenh
title: Kubectl CLI Tool
desc: 'Learn how to use the kubectl command line utility'
updated: 1646084541914
created: 1646083978256
---

The kubectl command line utility is designed to help you manage Kubernetes clusters.
You can perform common operations, such as create Pods and Services, using an imperative approach.
You can also apply Kubernetes manifest files from the filesystem or stored in memory.

### Apply Kubernetes Manifest with Kubectl

If your Kubernetes manifest file has a namespace declared in the `metadata` section of each resource, you can apply the template using the following command.

```
kubectl apply --filename mymanifest.yml
```

If resource definitions in your Kubernetes manifest do not contain a `metadata.namespace` setting, then you can specify the Kubernetes namespace that you want to deploy resources into.

```
kubectl apply --namespace mycustomapp --filename mymanifest.yml
```

You can also pipe a string, containing a Kubernetes manifest, into the kubectl utility. 
This option gives you more versatility over the source of a manifest file. 

```
@'
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - name: server
    image: nginx
'@ | kubectl apply --filename -
```
