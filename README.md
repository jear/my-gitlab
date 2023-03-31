# my-gitlab
```
helm upgrade --install my-gitlab gitlab/gitlab \
 -n my-gitlab --create-namespace \
 --timeout 600s  \
 --set global.hosts.domain=83-206-89-107.nip.io  \
 --set certmanager-issuer.email=jear@lysdemolab.fr \
 --set global.edition=ce  \
 --set global.initialRootPassword.secret=gitlab-initial-root-password \
 --set gitlab-runner.install=false \
 --set gitlab.unicorn.ingress.enabled=false \
 --set global.ingress.enabled=false  \
 --set nginx-ingress.enabled=false \
 --set registry.enabled=false  \
 --set prometheus.install=false \
 --set certmanager.install=false \
 -f sc-rook-values.yaml

```
