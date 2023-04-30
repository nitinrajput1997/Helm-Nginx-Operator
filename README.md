# Helm-Nginx-Operator

Initalize the operator:
```bash
operator-sdk init --domain nitinrajput.com --plugins helm
```

Create an API:
```bash
operator-sdk create api --group demo --version v1alpha1 --kind Nginx
```

Install Custom Resource Definition:
```bash
make install
```

Build and push operator docker image:
```bash
export IMG=nitinrajput658/nginx-helm-operator:0.0.1
make docker-build docker-push IMG=${IMG}
```

Deploy operator:
```bash
make deploy IMG=${IMG}
```

Install Custom Resource:
```bash
kubectl apply -f config/samples/demo_v1alpha1_nginx.yaml
```

### Uninstall

Delete Custom Resource:
```bash
kubectl delete -f config/samples/demo_v1alpha1_nginx.yaml
```

Delete operator:
```bash
make undeploy
```
