## Prerequisites

A Kubernetes Secret must be created with the following specification:

- Name: `aws-external-secrets-provider`
- Namespace: `flux-system`
- Type: `Opaque`
- Fields:
    - `aws-access-key-id`: base64-value
    - `aws-secret-access-key`: base64-value
