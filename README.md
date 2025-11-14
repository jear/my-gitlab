# my-gitlab
```
helm upgrade --install my-gitlab gitlab/gitlab \
 -n my-gitlab --create-namespace \
 --timeout 600s  \
 --set global.hosts.domain=gpu02.lysdemolab.fr  \
 --set certmanager-issuer.email=jear@lysdemolab.fr \
 --set global.hosts.externalIP=10.69.41.84 \
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
(base) ubuntu@my-ubuntu:~/workspace/github/my-gitlab$ k get pods -n my-gitlab
NAME                                            READY   STATUS      RESTARTS   AGE
my-gitlab-gitaly-0                              1/1     Running     0          11m
my-gitlab-gitlab-exporter-65dfcdb8d6-rtkts      1/1     Running     0          11m
my-gitlab-gitlab-shell-577684dffc-9nplf         1/1     Running     0          11m
my-gitlab-gitlab-shell-577684dffc-g25qr         1/1     Running     0          11m
my-gitlab-kas-5575644954-jrkgd                  1/1     Running     0          11m
my-gitlab-kas-5575644954-w2dsq                  1/1     Running     0          11m
my-gitlab-migrations-1-sb7jr                    0/1     Completed   0          11m
my-gitlab-minio-65bb67b6d4-kzdcd                1/1     Running     0          11m
my-gitlab-minio-create-buckets-1-wtxsl          0/1     Completed   0          11m
my-gitlab-postgresql-0                          2/2     Running     0          11m
my-gitlab-redis-master-0                        2/2     Running     0          11m
my-gitlab-sidekiq-all-in-1-v2-bd866cb6f-lm5tj   1/1     Running     0          11m
my-gitlab-toolbox-85969688cd-zcc6g              1/1     Running     0          11m
my-gitlab-webservice-default-69cb7447bc-m428m   2/2     Running     0          11m
my-gitlab-webservice-default-69cb7447bc-z7bdf   2/2     Running     0          11m

```

# Examples
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
