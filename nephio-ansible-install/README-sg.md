

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







kubectl --kubeconfig ~/.kube/mgmt-config port-forward --namespace=nephio-webui svc/nephio-webui 7007 &