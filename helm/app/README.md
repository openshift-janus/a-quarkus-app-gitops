# Install
## By helm cli
example:
```
  helm install a-quarkus-app . --set image.repository=image-registry.openshift-image-registry.svc:5000/a-quarkus-app-dev/a-quarkus-app --set image.tag=latest
```
# Why values-dev, -test, -prod.yaml?
This is because this same chart will be used for different env
It would be organized by upstream helm chart which generated argocd application which will specify the values-$env.yaml as helm parameters.
