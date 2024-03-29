# EKS helm deploy GitHub action

This action uses aws cli to login to EKS and deploy a helm chart.

## Inputs

### `aws-secret-access-key`

AWS secret access key part of the aws credentials. This is used to login to EKS.

### `aws-access-key-id`

AWS access key id part of the aws credentials. This is used to login to EKS.

### `aws-region`

AWS region to use. This must match the region your desired cluster lies in.

### `cluster-name`

The name of the desired cluster.

### `cluster-role-arn`

If you wish to assume an admin role, provide the role arn here to login as.

### `config-files`

Comma separated list of helm values files.

### `namespace`

Kubernetes namespace to use.

### `values`

Comma separates list of value set for helms. e.x: key1=value1,key2=value2

### `name`

The name of the helm deploy.

### `chart-path`

The path to the chart. (defaults to `helm/`)

### `argo-workflow`

if true, execute with `helm ... --post-renderer ./argo-post-renderer.sh`

## Example usage

```yaml
uses: markettrack/eks-helm-deploy@v2
with:
  aws-access-key-id: ${{ secrets.AWS_ACCESS__KEY_ID }}
  aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
  aws-region: us-west-2
  cluster-name: mycluster
  config-files: .github/values/dev.yaml
  namespace: dev
  values: key1=value1,key2=value2
  name: deploy_name
```
