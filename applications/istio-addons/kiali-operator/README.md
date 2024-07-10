https://kiali.io/docs/configuration/kialis.kiali.io/

## Validating Configuration

```bash
bash <(curl -sL https://raw.githubusercontent.com/kiali/kiali-operator/master/crd-docs/bin/validate-kiali-cr.sh) \
  -crd https://raw.githubusercontent.com/kiali/kiali-operator/master/crd-docs/crd/kiali.io_kialis.yaml \
  --kiali-cr-name kiali \
  -n istio-system
```
