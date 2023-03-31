# my-gitlab
```
helm upgrade --install my-gitlab gitlab/gitlab \
 -n my-gitlab --create-namespace \
 --timeout 600s  \
 --set global.hosts.domain=datasvc01.lysdemolab.fr  \
 --set certmanager-issuer.email=jear@lysdemolab.fr \
 --set global.hosts.externalIP=10.69.41.93 \
 --set global.ingress.configureCertmanager=false \
 --set global.hosts.https=false \
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


```
helm install gitlab gitlab/gitlab --namespace gitlab --wait --version 2.6.0 \
  --set certmanager.install=false \
  --set gitlab-runner.install=false \
  --set gitlab.gitaly.persistence.size=1Gi \
  --set gitlab.unicorn.ingress.enabled=false \
  --set global.appConfig.cron_jobs.ci_archive_traces_cron_worker.cron="17 * * * *" \
  --set global.appConfig.cron_jobs.expire_build_artifacts_worker.cron="50 * * * *" \
  --set global.appConfig.cron_jobs.pipeline_schedule_worker.cron="19 * * * *" \
  --set global.appConfig.cron_jobs.repository_archive_cache_worker.cron="0 * * * *" \
  --set global.appConfig.cron_jobs.repository_check_worker.cron="20 * * * *" \
  --set global.appConfig.cron_jobs.stuck_ci_jobs_worker.cron="0 * * * *" \
  --set global.appConfig.gravatar.plainUrl="https://www.gravatar.com/avatar/%{hash}?s=%{size}&d=identicon" \
  --set global.appConfig.gravatar.sslUrl="https://secure.gravatar.com/avatar/%{hash}?s=%{size}&d=identicon" \
  --set global.certificates.customCAs[0].secret=custom-ca \
  --set global.edition=ce \
  --set global.hosts.domain=${MY_DOMAIN} \
  --set global.ingress.configureCertmanager=false \
  --set global.ingress.enabled=false \
  --set global.initialRootPassword.secret=gitlab-initial-root-password \
  --set minio.persistence.size=5Gi \
  --set nginx-ingress.enabled=false \
  --set postgresql.persistence.size=1Gi \
  --set prometheus.install=false \
  --set redis.persistence.size=1Gi \
  --set registry.enabled=false
  ```
