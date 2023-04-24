

```
.68

sudo su -

cd /hone/telco/one-summit-22-workshop/nephio-ansible-install

pipenv shell

pip install ansible
pip install pygithub
pip install jmespath

ansible-galaxy collection install community.general
ansible-galaxy collection install community.docker

vagrant up

ssh -4 -L37007:192.168.56.60:7007 vagrant@192.168.56.60

vagrant ssh
```

```
apiVersion: v1
kind: Service
metadata:
  name: nephio-webui-ext
  namespace: nephio-webui
spec:
  type: NodePort
  selector:
    app: nephio-webui
  ports:
    - name: http
      port: 7007
      nodePort: 32555
      targetPort: http
```




```
kubectl --kubeconfig ~/.kube/mgmt-config get clusters.infra.nephio.org --all-namespaces -o yaml

kubectl --kubeconfig ~/.kube/mgmt-config get upfdeployments --all-namespaces -o yaml
apiVersion: v1
items: []
kind: List
metadata:
  resourceVersion: ""
   

   --> shouldn't be empty!


kubectl --kubeconfig ~/.kube/mgmt-config get packagedeployments --all-namespaces -o yaml
apiVersion: v1
items:
- apiVersion: automation.nephio.org/v1alpha1
  kind: PackageDeployment
  metadata:
    annotations:
      nf.nephio.org/cluster-set: agg-layer
      nf.nephio.org/topology: fivegcoretopology-sample
      nf.nephio.org/type: UPF
    creationTimestamp: "2023-04-21T15:14:12Z"
    generation: 1
    name: fivegcoretopology-sample-agg-layer
    namespace: default
    ownerReferences:
    - apiVersion: nf.nephio.org/v1alpha1
      blockOwnerDeletion: true
      controller: true
      kind: FiveGCoreTopology
      name: fivegcoretopology-sample
      uid: 82f19dd1-4ec0-465b-84f5-06f3609bee91
    resourceVersion: "2903"
    uid: 0a9920cf-d6e9-4d8e-895f-6014eecd24b6
  spec:
    annotations:
      nf.nephio.org/cluster-set: agg-layer
      nf.nephio.org/topology: fivegcoretopology-sample
      nf.nephio.org/type: UPF
    name: agg-layer-upf
    namespace: upf
    packageRef:
      packageName: free5gc-upf
      repository: free5gc-packages
      revision: v1
    selector:
      matchLabels:
        nephio.org/region: us-central1
        nephio.org/site-type: edge
kind: List
metadata:
  resourceVersion: ""





kubectl --kubeconfig ~/.kube/mgmt-config port-forward --namespace=nephio-webui svc/nephio-webui 7007 &
```



# Findings

https://github.com/nephio-project/nf-deploy-controller
  NF type, flavour etc similar to our NSDs
