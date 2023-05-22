# Hashicorp Boundary

## Description

A Helm chart for Hashicorp Boundary deployment

(This is based on previous work by https://github.com/ugns/boundary-chart)

## Usage

Please add the Vertigo repository before installing any chart provided by this repository:

```sh
helm repo add vertigo https://vertigo.github.io/charts
helm repo update
```

### Installing the Chart

To install the chart with the release name boundary run:

```sh
helm install boundary vertigo/boundary
```

Please notice Boundary requires a postgres database that must be previously available.

## Development

To install this chart during development use the local folders:

```sh
helm install boundary ./boundary
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| aead.enabled | bool | `true` | to enable AEAD KMS keys |
| affinity | object | `{}` |  |
| awskms.enabled | bool | `false` | to enable AWS KMS keys |
| controller.autoscaling.enabled | bool | `false` |  |
| controller.autoscaling.maxReplicas | int | `100` |  |
| controller.autoscaling.minReplicas | int | `1` |  |
| controller.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| controller.enabled | bool | `true` | Specifies whether Boundary controller should be deployed |
| controller.ingress.annotations | object | `{}` |  |
| controller.ingress.className | string | `""` |  |
| controller.ingress.enabled | bool | `false` |  |
| controller.ingress.hosts[0].host | string | `"boundary.local"` |  |
| controller.ingress.hosts[0].paths[0].path | string | `"/"` |  |
| controller.ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| controller.ingress.hosts[0].paths[0].port | string | `"api"` |  |
| controller.ingress.tls | list | `[]` |  |
| controller.initOptions | list | `[]` | List of options to enable for `boundary database init` call on a fresh installation |
| controller.replicaCount | string | `nil` |  |
| controller.service.annotations | object | `{}` |  |
| controller.service.ports.api.number | int | `9200` |  |
| controller.service.ports.cluster.number | int | `9201` |  |
| controller.service.type | string | `"ClusterIP"` |  |
| database.address | string | `"postgresql"` | the Boundary database hostname |
| database.name | string | `"boundary"` | the Boundary databse name |
| database.password | string | `"postgres"` | the Boundary database password to use. ignored if using Vault |
| database.ssl | bool | `false` | Specify if sslmode should be enabled |
| database.username | string | `"postgres"` | the Boundary database username to use. ignored if using Vault |
| fullnameOverride | string | `""` |  |
| global.replicaCount | int | `3` |  |
| image.pullPolicy | string | `"IfNotPresent"` | the docker image pull policy |
| image.repository | string | `"hashicorp/boundary"` | The docker image repository to use |
| image.tag | string | Chart appVersion | the docker image tag to use  |
| imagePullSecrets | list | `[]` |  |
| keys.aead | list | `[]` | the AEAD KMS keys to configure if enabled |
| keys.awskms | list | `[]` | the AWS KMS keys to configure if enabled |
| keys.vault | list | `[]` | the Hashicorp Vault Transit KMS keys to configure if enabled |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecrets | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` |  |
| vault.address | string | `"http://vault:8200"` | the Hashicorp Vault address to use |
| vault.database.enabled | bool | `false` | to enable Hashicorp Vault lookup for database credentials |
| vault.database.role | string | `"boundary"` | Hashicorp Vault Postgres Database Secret role to use |
| vault.database.vaultAdminCredPath | string | `"database/static-creds/boundary-db"` | Hashicorp Vault secret path for Boundary database admin credentials |
| vault.database.vaultCredPath | string | `"database/creds/boundary-db"` | Hashicorp Vault secret path for Boundary database credentials |
| vault.enabled | bool | `false` | to enable Hashicorp Vault for Transit KMS keys and database credentials |
| vault.tls | object | `{}` | the Hashicorp Vault TLS settings to use |
| worker.autoscaling.enabled | bool | `false` |  |
| worker.autoscaling.maxReplicas | int | `100` |  |
| worker.autoscaling.minReplicas | int | `1` |  |
| worker.autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| worker.enabled | bool | `true` |  |
| worker.ingress.annotations | object | `{}` |  |
| worker.ingress.className | string | `""` |  |
| worker.ingress.enabled | bool | `false` |  |
| worker.ingress.hosts[0].host | string | `"boundary.local"` |  |
| worker.ingress.hosts[0].paths[0].path | string | `"/"` |  |
| worker.ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| worker.ingress.hosts[0].paths[0].port | string | `"proxy"` |  |
| worker.ingress.tls | list | `[]` |  |
| worker.replicaCount | string | `""` |  |
| worker.service.annotations | object | `{}` |  |
| worker.service.ports.proxy.number | int | `9202` |  |
| worker.service.type | string | `"ClusterIP"` |  |

**Homepage:** <https://boundaryproject.io>

## Source Code

* <https://github.com/hashicorp/boundary>
* <https://github.com/vertigobr/boundary-chart>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Jeremy T. Bouse | <Jeremy.Bouse@UnderGrid.net> | <https://undergrid.net> |
