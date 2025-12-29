# my-gitlab
```
https://cert-manager.io/docs/installation/
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.19.1/cert-manager.yaml

https://docs.gitlab.com/operator/installation/?tab=Helm+Chart#installing-the-gitlab-operator


helm repo add gitlab https://charts.gitlab.io
helm repo update

#    version: "X.Y.Z" # https://gitlab.com/gitlab-org/cloud-native/gitlab-operator/-/blob/<OPERATOR_VERSION>/CHART_VERSIONS

helm search repo gitlab-operator -l | head
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
gitlab/gitlab-operator  2.5.2           2.5.2           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.5.1           2.5.1           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.5.0           2.5.0           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.4.2           2.4.2           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.4.1           2.4.1           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.4.0           2.4.0           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.3.2           2.3.2           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.3.1           2.3.1           The GitLab operator aims to manage the full lif...
gitlab/gitlab-operator  2.3.0           2.3.0           The GitLab operator aims to manage the full lif...


helm search repo gitlab -l | head
NAME                            CHART VERSION   APP VERSION     DESCRIPTION
gitlab/gitlab                   9.5.2           v18.5.2         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.5.1           v18.5.1         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.5.0           v18.5.0         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.4.4           v18.4.4         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.4.3           v18.4.3         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.4.2           v18.4.2         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.4.1           v18.4.1         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.4.0           v18.4.0         GitLab is the most comprehensive AI-powered Dev...
gitlab/gitlab                   9.3.6           v18.3.6         GitLab is the most comprehensive AI-powered Dev...


https://gitlab.com/gitlab-org/cloud-native/gitlab-operator/-/blob/master/deploy/chart/values.yaml

https://docs.gitlab.com/charts/installation/tls/#option-2-use-your-own-wildcard-certificate

kubectl create secret tls <tls-secret-name> --cert=<path/to-full-chain.crt> --key=<path/to.key>
helm upgrade --install install gitlab gitlab/gitlab \
  --set installCertmanager=false \
  --set global.ingress.configureCertmanager=false \
  --set global.ingress.tls.secretName=<tls-secret-name>


helm upgrade --install gitlab-operator gitlab/gitlab-operator  --namespace gitlab-system  --create-namespace
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

