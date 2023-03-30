# my-gitlab
```
helm upgrade --install my-gitlab gitlab/gitlab \
 -n my-gitlab --create-namespace \
 --timeout 600s  \
 --set global.hosts.domain=gitlab.datasvc01.lysdemolab.fr  \
 --set certmanager-issuer.email=jerome.armand@hpe.com \
 --set global.edition=ce  \
 --set global.initialRootPassword.secret=gitlab-initial-root-password \
 --set gitlab-runner.install=false \
 --set gitlab.unicorn.ingress.enabled=false \
 --set global.ingress.enabled=false  \
 --set nginx-ingress.enabled=false \
 --set registry.enabled=false  \
 --set prometheus.install=false \
 --set certmanager.install=false \
 --set gitlab-runner.install=false \
 -f sc-rook-values.yaml

```
