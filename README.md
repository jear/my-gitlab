# my-gitlab
```
helm upgrade --install my-gitlab gitlab/gitlab \
 -n my-gitlab --create-namespace \
 --timeout 600s  \
 --set global.hosts.domain=datasvc01.lysdemolab.fr  \
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


WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /home/ubuntu/.kube/datasvc01.yaml
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /home/ubuntu/.kube/datasvc01.yaml
Release "my-gitlab" does not exist. Installing it now.
NAME: my-gitlab
LAST DEPLOYED: Fri Mar 31 14:16:50 2023
NAMESPACE: my-gitlab
STATUS: deployed
REVISION: 1
NOTES:
=== NOTICE
The minimum required version of PostgreSQL is now 12. See https://gitlab.com/gitlab-org/charts/gitlab/-/blob/master/doc/installation/upgrade.md for more details.
Help us improve the installation experience, let us know how we did with a 1 minute survey:https://gitlab.fra1.qualtrics.com/jfe/form/SV_6kVqZANThUQ1bZb?installation=helm&release=15-9

=== NOTICE
kas:
    The configuration of `gitlab.kas.privateApi.tls.enabled` has moved. Please use `global.kas.tls.enabled` instead.
    Other components of the GitLab chart other than KAS also need to be configured to talk to KAS via TLS.
    With a global value the chart can take care of these configurations without the need for other specific values.

```
