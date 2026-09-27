# Projects helm chart

## Parameters

### General configuration

| Name                                  | Description                                          | Value                  |
| ------------------------------------- | ---------------------------------------------------- | ---------------------- |
| `image.repository`                    | Repository to use to pull projects's container image | `ghcr.io/wqrld/projects` |
| `image.tag`                           | projects's container tag                             | `latest`               |
| `image.pullPolicy`                    | Container image pull policy                          | `IfNotPresent`         |
| `image.credentials.username`          | Username for container registry authentication       |                        |
| `image.credentials.password`          | Password for container registry authentication       |                        |
| `image.credentials.registry`          | Registry url for which the credentials are specified |                        |
| `image.credentials.name`              | Name of the generated secret for imagePullSecrets    |                        |
| `nameOverride`                        | Override the chart name                              | `""`                   |
| `fullnameOverride`                    | Override the full application name                   | `""`                   |
| `ingress.enabled`                     | whether to enable the Ingress or not                 | `false`                |
| `ingress.className`                   | IngressClass to use for the Ingress                  | `nil`                  |
| `ingress.host`                        | Host for the Ingress                                 | `projects.example.com` |
| `ingress.path`                        | Path to use for the Ingress                          | `/`                    |
| `ingress.hosts`                       | Additional host to configure for the Ingress         | `[]`                   |
| `ingress.tls.enabled`                 | Whether to enable TLS for the Ingress                | `true`                 |
| `ingress.tls.secretName`              | Secret name for TLS config                           | `nil`                  |
| `ingress.tls.additional[].secretName` | Secret name for additional TLS config                |                        |
| `ingress.tls.additional[].hosts[]`    | Hosts for additional TLS config                      |                        |
| `ingress.customBackends`              | Add custom backends to ingress                       | `[]`                   |

### backend

| Name                                                  | Description                                                                        | Value            |
| ----------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------- |
| `backend.command`                                     | Override the backend container command                                             | `[]`             |
| `backend.args`                                        | Override the backend container args                                                | `[]`             |
| `backend.replicas`                                    | Amount of backend replicas. More than one requires REDIS_URL and S3 storage        | `1`              |
| `backend.shareProcessNamespace`                       | Enable share process namespace between containers                                  | `false`          |
| `backend.sidecars`                                    | Add sidecars containers to backend deployment                                      | `[]`             |
| `backend.securityContext.allowPrivilegeEscalation`    | Whether to allow privilege escalation for the backend container                    | `false`          |
| `backend.securityContext.capabilities.drop`           | List of capabilities to drop for the backend container                             | `["ALL"]`        |
| `backend.securityContext.runAsNonRoot`                | Whether to run the backend container as a non-root user                            | `true`           |
| `backend.securityContext.seccompProfile.type`         | Seccomp profile type for the backend container                                     | `RuntimeDefault` |
| `backend.envVars`                                     | Configure backend container environment variables                                  | `undefined`      |
| `backend.envVars.BY_VALUE`                            | Example environment variable by setting value directly                             |                  |
| `backend.envVars.FROM_CONFIGMAP.configMapKeyRef.name` | Name of a ConfigMap when configuring env vars from a ConfigMap                     |                  |
| `backend.envVars.FROM_CONFIGMAP.configMapKeyRef.key`  | Key within a ConfigMap when configuring env vars from a ConfigMap                  |                  |
| `backend.envVars.FROM_SECRET.secretKeyRef.name`       | Name of a Secret when configuring env vars from a Secret                           |                  |
| `backend.envVars.FROM_SECRET.secretKeyRef.key`        | Key within a Secret when configuring env vars from a Secret                        |                  |
| `backend.podAnnotations`                              | Annotations to add to the backend Pod                                              | `{}`             |
| `backend.dpAnnotations`                               | Annotations to add to the backend Deployment                                       | `{}`             |
| `backend.service.type`                                | backend Service type                                                               | `ClusterIP`      |
| `backend.service.port`                                | backend Service listening port                                                     | `80`             |
| `backend.service.targetPort`                          | backend container listening port                                                   | `1337`           |
| `backend.service.annotations`                         | Annotations to add to the backend Service                                          | `{}`             |
| `backend.probes.liveness.path`                        | Configure path for backend HTTP liveness probe                                     | `/`              |
| `backend.probes.liveness.targetPort`                  | Configure port for backend HTTP liveness probe                                     | `nil`            |
| `backend.probes.liveness.initialDelaySeconds`         | Configure initial delay for backend liveness probe                                 | `10`             |
| `backend.probes.liveness.timeoutSeconds`              | Configure timeout for backend liveness probe                                       | `nil`            |
| `backend.probes.startup.path`                         | Configure path for backend HTTP startup probe                                      |                  |
| `backend.probes.startup.targetPort`                   | Configure port for backend HTTP startup probe                                      |                  |
| `backend.probes.startup.initialDelaySeconds`          | Configure initial delay for backend startup probe                                  |                  |
| `backend.probes.startup.timeoutSeconds`               | Configure timeout for backend startup probe                                        |                  |
| `backend.probes.readiness.path`                       | Configure path for backend HTTP readiness probe                                    | `/`              |
| `backend.probes.readiness.targetPort`                 | Configure port for backend HTTP readiness probe                                    | `nil`            |
| `backend.probes.readiness.initialDelaySeconds`        | Configure initial delay for backend readiness probe                                | `10`             |
| `backend.probes.readiness.timeoutSeconds`             | Configure timeout for backend readiness probe                                      | `nil`            |
| `backend.resources`                                   | Resource requirements for the backend container                                    | `{}`             |
| `backend.nodeSelector`                                | Node selector for the backend Pod                                                  | `{}`             |
| `backend.tolerations`                                 | Tolerations for the backend Pod                                                    | `[]`             |
| `backend.affinity`                                    | Affinity for the backend Pod                                                       | `{}`             |
| `backend.persistence`                                 | Additional volumes to create and mount on the backend. Used for debugging purposes | `{}`             |
| `backend.persistence.volume-name.size`                | Size of the additional volume                                                      |                  |
| `backend.persistence.volume-name.type`                | Type of the additional volume, persistentVolumeClaim or emptyDir                   |                  |
| `backend.persistence.volume-name.mountPath`           | Path where the volume should be mounted to                                         |                  |
| `backend.extraVolumeMounts`                           | Additional volumes to mount on the backend.                                        | `[]`             |
| `backend.extraVolumes`                                | Additional volumes to mount on the backend.                                        | `[]`             |
| `backend.pdb.enabled`                                 | Enable pdb on backend                                                              | `true`           |
| `backend.serviceAccountName`                          | Optional service account name to use for backend pods                              | `nil`            |
