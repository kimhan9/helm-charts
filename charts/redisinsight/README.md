# Redisinsight Helm chart

Based on [heywood8/redisinsight](https://github.com/heywood8/helm-charts/tree/main/charts/redisinsight)

Redis Insight for Redis.

## Usage

### Install Chart

```console
helm install redisinsight kimhan9/redisinsight
```

### Uninstall Chart

```console
helm uninstall redisinsight
```

## Configuration

Example configuration:

```yaml
image:
    repository: redis/redisinsight
    tag: 3.8
service:
    port: 5540
volumeMount:
    mountPath: /data
nodeSelector:
    workload-type: general
volume:
    enabled: true
    name: redisinsight
    size: 1Gb
initContainers:
- name: init
    image: busybox
    command: ["/bin/sh", "-c", "chown -R 1000 /data"]
    volumeMounts:
    - mountPath: "/data"
        name: redisinsight
```
