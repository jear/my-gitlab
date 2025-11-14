# my-gitlab
```
https://cert-manager.io/docs/installation/
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.19.1/cert-manager.yaml

https://docs.gitlab.com/operator/installation/?tab=Helm+Chart#installing-the-gitlab-operator


helm repo add gitlab https://charts.gitlab.io
helm repo update


https://gitlab.com/gitlab-org/cloud-native/gitlab-operator/-/blob/master/deploy/chart/values.yaml

helm install gitlab-operator gitlab/gitlab-operator   --create-namespace   --namespace gitlab-system
W1114 10:38:35.678159   46055 warnings.go:70] spec.privateKey.rotationPolicy: In cert-manager >= v1.18.0, the default value changed from `Never` to `Always`.
NAME: gitlab-operator
LAST DEPLOYED: Fri Nov 14 10:38:33 2025
NAMESPACE: gitlab-system
STATUS: deployed
REVISION: 1
TEST SUITE: None


https://docs.gitlab.com/charts/charts/

kubectl -n gitlab-system apply -f mygitlab.yaml

```

