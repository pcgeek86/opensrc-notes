---
id: xS4a2VvW7vHG500rq8Ae0
title: Deploying Kubernetes Pods
desc: Deploying pods onto Kubernetes clusters.
updated: 1645838207608
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

### Deploy MySQL Database in Kubernetes Pod

The following Kubernetes manifest will deploy a Kubernetes pod running the MySQL database engine.

```yml
apiVersion: v1
kind: Pod
metadata:
  name: mysqlserver # Name for the Kubernetes pod
  labels:
    purpose: Store financial data # A key-value label for the MySQL pod
spec:
  containers:
  - name: mysqldb
    image: mysql:latest
    env:
      - name: MYSQL_ROOT_PASSWORD
        value: --yourpasswordhere--
```

### Deploy Pod Manifest with PowerShell

You can pipe a Kubernetes manifest directly into PowerShell.
To accomplish this, set the `--filename` parameter to a `-` dash character, and pipe the string into the `kubectl` command.

```powershell
@'
apiVersion: v1
kind: Pod
metadata:
  name: mysqlserver                    # Name for the Kubernetes pod
  labels:
    purpose: store-financial-data      # A key-value label for the MySQL pod
spec:
  containers:
  - name: mysqldb
    image: mysql:latest
    env:
      - name: MYSQL_ROOT_PASSWORD      # The MySQL container image requires that you set a root password statically or randomly. This is the static method
        value: --yourpasswordhere--    # The root password for the MySQL engine
'@ | kubectl apply --filename -
```

### Deploy Kubernetes Pod with Multiple Containers

You can deploy more than one container in each Kubernetes Pod resource.
The `containers` property on the Kubernetes Pod spec is an array, so all you need to do is add more containers.
Keep in mind that a Pod has a single IP address, and two containers cannot use the same network port.

