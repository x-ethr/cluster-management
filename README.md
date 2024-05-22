# cluster-management

Kubernetes GitOps for Management Cluster(s)

## New Cluster Provisioning

```bash
flux bootstrap github --repository "https://github.com/iac-factory/cluster-management" \
    --owner "iac-factory" \
    --private "false" \
    --personal "false" \
    --path "clusters/local"
```
