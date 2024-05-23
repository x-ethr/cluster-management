# cluster-management

Kubernetes GitOps for Management Cluster(s)

## Task-Board

- [ ] Secure Grafana Installation
    - [ ] Establish Independent Grafana Application 
    - [ ] Remove `grafana.yaml` from `istio` Application

## New Cluster Provisioning

*Local* - Create cluster.

```bash
kind create cluster --config "configuration.yaml"
kubectl config set-context "$(printf "%s-kind" "kind")"
```

Bootstrap.
```bash
flux bootstrap github --repository "https://github.com/iac-factory/cluster-management" \
    --owner "iac-factory" \
    --private "false" \
    --personal "false" \
    --path "clusters/local"
```

Sync local cluster repository's `vendors`.
```bash
git submodule update --remote --recursive
```

Add `kustomization.yaml` to new cluster directory.

```bash
cat << EOF > ./vendors/cluster-management/clusters/local/kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources: []
EOF
```

Update.

```bash
git submodule foreach "git add . && git commit --message \"Git Submodule Update(s)\" && git push -u origin HEAD:main" 
```

## References

- https://kiali.io/docs/configuration/kialis.kiali.io/#example-cr
