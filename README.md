# helmfile-local-example
Example of using helmfile to deploy local manifests

## helmfile diff
my favorite helmfile command 

```
➜  helmfile-local-example git:(main) ✗ helmfile diff                                                                                                       
Building dependency release=helmfile-local-example, chart=.
Comparing release=helmfile-local-example, chart=.
********************

        Release was not present in Helm.  Diff will show entire contents as new.

********************
example, ubuntu, Pod (v1) has been added:
- 
+ # Source: helmfile-local-example/templates/manifest.yaml
+ apiVersion: v1
+ kind: Pod
+ metadata:
+   name: ubuntu
+   labels:
+     app: ubuntu
+ spec:
+   restartPolicy: Always
+   containers:
+   - image: ubuntu
+     command:
+       - "sleep"
+       - "infinity"
+     imagePullPolicy: IfNotPresent
+     name: ubuntu
+     resources:
+       requests:
+         memory: "64Mi"
+         cpu: "250m"
+       limits:
+         memory: "128Mi"
+         cpu: "500m"
```


## what it deploys 

```
➜  helmfile-local-example git:(main) ✗ k get po -n example                                                                                                 
NAME     READY   STATUS    RESTARTS   AGE
ubuntu   1/1     Running   0          34s
```
