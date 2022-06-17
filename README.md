# Consul Package 

Consul is an open source object-relational database known for reliability and data integrity. ACID-compliant, it supports foreign keys, joins, views, triggers and stored procedures.

## Configuration Reference

You can configure the following:

### Consul common paramerers 

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|datacenterName|Datacenter name for Consul. If not supplied, will use the Consul|string|dc1|
|domain|Consul domain name|string|consul|
|raftMultiplier|Multiplier used to scale key Raft timing parameters|integer|1|
|gossipKey|Gossip key for all members. The key must be 16-bytes, can be generated with $(consul keygen)|string|""|
|tlsEncryptionSecretName|Name of existing secret with TLS encryption data|string|""|
|configuration|HashiCorp Consul configuration to be injected as ConfigMap|string|""|
|existingConfigmap|ConfigMap with HashiCorp Consul configuration|string|""|
|localConfig|Extra configuration that will be added to the default one|string|""|
|podLabels|Pod labels|string|{}|
|priorityClassName|Priority class assigned to the Pods|string|""|
|schedulerName|Alternative scheduler|string|""|
|terminationGracePeriodSeconds|In seconds, time the given to the Consul pod needs to terminate gracefully|string|""|
|extraEnvVarsCM|Name of existing ConfigMap containing extra env vars|string|""|
|extraEnvVarsSecret|Name of existing Secret containing extra env vars|string|""|
|containerPorts.http|Port to open for HTTP in Consul|integer|8500|
|containerPorts.dns|"Port to open for DNS server in Consul"|integer|8600|
|containerPorts.rpc|"Port to open for RPC in Consul"|integer|8400|
|containerPorts.rpcServer|Port to open for RPC Server in Consul|integer|8300|
|containerPorts.serfLAN|Port to open for Serf LAN in Consul|integer|8301|
|lifecycleHooks|Add lifecycle hooks to the deployment|string|{}|

### Statefulset parameters


|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|replicaCount|Number of HashiCorp Consul replicas to deploy|integer|3|
|updateStrategy.type|Update strategy type for the HashiCorp Consul statefulset|string|RollingUpdate|
|podManagementPolicy|StatefulSet pod management policy|string|Parallel|
|podAnnotations|Additional pod annotations|string|{}|
|podAntiAffinityPreset|Pod anti-affinity preset. Ignored if affinity affinity soft  or hard|string|soft|
|nodeAffinityPreset.type|Node affinity preset type. Ignored if  affinity  is set. Allowed values:  soft  or  hard|string|""|
|nodeAffinityPreset.key|Node label key to match. Ignored if  affinity is set|string|""|
|affinity|Affinity for pod assignment|string|{}|
|nodeSelector|Node labels for pod assignment|string|{}|
|podSecurityContext.enabled|Enable security context for HashiCorp Consul pods|string|true|
|podSecurityContext.fsGroup|Group ID for the volumes of the pod|integer|1001|
|containerSecurityContext.enabled|HashiCorp Consul Container securityContext|string|true|
|containerSecurityContext.runAsUser|User ID for the HashiCorp Consul container|integer|1001|
|containerSecurityContext.runAsNonRoot|Force the container to be run as non root|string|true|
|resources.limits|"The resources limits for HashiCorp Consul containers"|string|{}|
|resources.requests|The requested resources for HashiCorp Consul containers|string|{}|
|livenessProbe.enabled|"Enable livenessProbe	"|string|true|
|livenessProbe.initialDelaySeconds|livenessProbe.initialDelaySeconds|integer|30|
|livenessProbe.periodSeconds|Period seconds for livenessProbe|integer|10|
|livenessProbe.timeoutSeconds|Timeout seconds for livenessProbe|integer|5|
|livenessProbe.failureThreshold|Failure threshold for livenessProbe|integer|6|
|livenessProbe.successThreshold|Success threshold for livenessProbe|integer|1|
|readinessProbe.enabled|Enable readinessProbe|string|true|
|readinessProbe.initialDelaySeconds|Initial delay seconds for readinessProbe|integer|5|
|readinessProbe.periodSeconds|Period seconds for readinessProbe|integer|10|
|readinessProbe.timeoutSeconds|Timeout seconds for readinessProbe|integer|5|
|readinessProbe.failureThreshold|Failure threshold for readinessProbe|integer|6|
|readinessProbe.successThreshold|Success threshold for readinessProbe|integer|1|
|startupProbe.enabled|Enable startupProbe|string|false|
|startupProbe.initialDelaySeconds|Initial delay seconds for startupProbe|integer|0|
|startupProbe.periodSeconds|Period seconds for startupProbe|integer|10|
|startupProbe.timeoutSeconds|Timeout seconds for startupProbe|integer|5|
|startupProbe.failureThreshold|Failure threshold for startupProbe|integer|60|
|startupProbe.successThreshold|Success threshold for startupProbe|integer|1|
|customLivenessProbe|Override default liveness probe|string|{}|
|customReadinessProbe|Override default readiness probe|string|{}|
|customStartupProbe|Override default startup probe|string|{}|
|pdb.create|Enable/disable a Pod Disruption Budget creation|string|false|
|pdb.minAvailable|"Minimum number of pods that must still be available after the eviction	"|integer|1|
|pdb.maxUnavailable|Max number of pods that can be unavailable after the eviction|string|""|
|resources.limits|The resources limits for HashiCorp Consul containers|string|""|
|resources.requests|The requested resources for HashiCorp Consul containers|string|{}|
|containerSecurityContext.enabled|HashiCorp Consul Container securityContext|string|true|
|containerSecurityContext.runAsUser|User ID for the HashiCorp Consul container|integer|1001|
|containerSecurityContext.runAsNonRoot|Force the container to be run as non root|string|true|


### Exposure parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|service.enabled|Use a service to access HashiCorp Consul Ui|string|true|
|service.ports.http|HashiCorp Consul UI svc port|integer|true|
|service.type|HashiCorp Consul UI Service Type|string|ClusterIP|
|service.nodePorts.http|Node port for HashiCorp Consul UI|""|
|service.clusterIP|Consul service Cluster IP|string|""|
|serviceservice.sessionAffinity|Session Affinity for Kubernetes service, can be "None" or "ClientIP"|string|none|
|ingress.enabled|Enable ingress resource for Management console|string|false|
|ingress.path|Path for the default host|string|/|
|ingress.apiVersion|Override API Version (automatically detected if not set)|string|""|
|ingress.pathType|Ingress path type|string|ImplementationSpecific|
|ingress.hostname|Default host for the ingress resource, a host pointing to this will be created|string|consul-ui.local|
|ingress.annotations|Additional annotations for the Ingress resource. To enable certificate autogeneration, place here your cert-manager annotations.|string|{}|
|ingress.ingressClassName|Set the ingerssClassName on the ingress record for k8s 1.18+|string|""|
|ingress.tls|Enable TLS configuration for the hostname defined at ingress.hostname parameter|string|false|
|ingress.selfSigned|Create a TLS secret for this ingress record using self-signed certificates generated by Helm|string|false|
|ingress.existingSecret|It is you own the certificate as secret.|string|""|
|service.loadBalancerIP|HashiCorp Consul UI service Load Balancer IP|string|""|
|servic.annotations|Annotations for HashiCorp Consul UI service|string|{}|
|service.externalTrafficPolicy|Service external traffic policy|string|cluster|
|service.sessionAffinityConfig|Additional settings for the sessionAffinity|string|{}|
|service.sessionAffinity|Session Affinity for Kubernetes service, can be "None" or "ClientIP"|string|none|
|ingress.enabled|Enable ingress resource for Management console|string|false|
|ingress.path|Path for the default host|string|/|
|ingress.apiVersion|Override API Version (automatically detected if not set)|string|""|
|ingress.pathType|Ingress path type|string|ImplementationSpecific|
|ingress.hostname|Default host for the ingress resource, a host pointing to this will be created|string|consul-ui.local|
|ingress.annotations|Additional annotations for the Ingress resource. To enable certificate autogeneration, place here your cert-manager annotations.|string|{}|
|ingress.ingressClassName|Set the ingerssClassName on the ingress record for k8s 1.18+|string|""|
|ingress.tls|Enable TLS configuration for the hostname defined at ingress.hostname parameter|string|false|
|ingress.selfSigned|Create a TLS secret for this ingress record using self-signed certificates generated by Helm|string|false|
|ingress.existingSecret|It is you own the certificate as secret.|string|""|


### Persistence parameters


|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|persistence.enabled|Enable HashiCorp Consul data persistence using PVC, use a Persistent Volume Claim, If false, use emptyDir|string|true|
|persistence.storageClass|Persistent Volume storage class|string|""|
|"persistence.annotations	"|Persistent Volume Claim annotations|string|{}|
|persistence.accessModes|Persistent Volume Access Mode|string|["ReadWriteOnce"]|
|persistence.size|PVC Storage Request for HashiCorp Consul data volume|integer|8Gi|


###  Volume Permissions parameters


|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|volumePermissions.enabled|Enable init container that changes the owner and group of the persistent volume|string|false|
|volumePermissions.image.registry|Bitnami Shell image registry|string|"docker.io"|
|volumePermissions.image.repository|Bitnami Shell image repository|string|bitnami/bitnami-shell|
|"volumePermissions.image.tag	"|Bitnami Shell image tag (immutable tags are recommended)|string|10-debian-10-r435|
|volumePermissions.image.pullPolicy|Bitnami Shell image pull policy|string|IfNotPresent|

####  Metrics parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|metrics.enabled|Start a side-car prometheus exporter|string|false|
|metrics.image.registry|HashiCorp Consul Prometheus Exporter image registry|string|docker.io|
|metrics.image.repository|HashiCorp Consul Prometheus Exporter image repository|string|bitnami/consul-exporter|
|metrics.image.tag|HashiCorp Consul Prometheus Exporter image tag (immutable tags are recommended)|string|0.8.0-debian-10-r99|
|metrics.image.pullPolicy|HashiCorp Consul Prometheus Exporter image pull policy|string|IfNotPresent|
|metrics.serviceMonitor.enabled|Create ServiceMonitor Resource for scraping metrics using PrometheusOperator, set to true to create a Service Monitor Entry|string|false|
|metrics.serviceMonitor.namespace|The namespace in which the ServiceMonitor will be created|string|""|
|metrics.serviceMonitor.interval|Interval at which metrics should be scraped|integer|30s|
|metrics.serviceMonitor.scrapeTimeout|The timeout after which the scrape is ended|string|""|
|metrics.serviceMonitor.honorLabels|Specify honorLabels parameter to add the scrape endpoint|string|false|
|metrics.serviceMonitor.jobLabel|The name of the label on the target service to use as the job name in prometheus.|string|""|
|metrics.serviceMonitor.selector|ServiceMonitor selector labels|string|{}|
|metrics.serviceMonitor.labels|Used to pass Labels that are used by the Prometheus installed in your cluster to select Service Monitors to work with|string|{}|

###  statefulset Parameter
|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|env.BITNAMI_DEBUG|statefulset env BITNAMI_DEBUG|string|false|
|env.CONSUL_NODE_NAME|statefulset env CONSUL_NODE_NAME|string|metadata.name|
|env.CONSUL_BOOTSTRAP_EXPECT|statefulset env CONSUL_BOOTSTRAP_EXPECT|integer|3|
|env.CONSUL_RETRY_JOIN|statefulset env CONSUL_RETRY_JOIN|string|release-name-consul-headless.default.svc.cluster.local|
|env.CONSUL_DISABLE_KEYRING_FILE|statefulset env CONSUL_DISABLE_KEYRING_FILE|string|true|
|env.CONSUL_RAFT_MULTIPLIER|statefulset env CONSUL_RAFT_MULTIPLIER|integer|1|
|env.CONSUL_DOMAIN|statefulset env CONSUL_DOMAIN|string|consul|
|env.CONSUL_DATACENTER|statefulset env CONSUL_DATACENTER|string|dc1|
|env.CONSUL_UI|statefulset env CONSUL_UI|string|true|
|env.CONSUL_HTTP_PORT_NUMBER|statefulset env CONSUL_HTTP_PORT_NUMBER|integer|8500|
|env.CONSUL_DNS_PORT_NUMBER|statefulset env CONSUL_DNS_PORT_NUMBER|integer|8600|
|env.CONSUL_RPC_PORT_NUMBER|statefulset env CONSUL_RPC_PORT_NUMBER|integer|8400|
|env.CONSUL_SERF_LAN_PORT_NUMBER|statefulset env CONSUL_SERF_LAN_PORT_NUMBER"|integer|8301|


### Common parameters

|Parameter|Description|Type|Default|
|---------|-----------|----|-------|
|imagePullPolicy|imagePullPolicy|string|IfNotPresent|
|volumeClaimTemplates.storage|Volume storage|integer|8Gi|
|securityContext.runAsUser|runAsUser|integer|1001|
|ports.containerPort|containerPort|integer|9107
|prometheusioport|prometheusioport|integer|9107|
|prometheusioscrape|prometheusioscrape|string|true|
|volumeMounts.mountPath| Voulme Mount Path|string|/bitnami/consul|
|initContainers.enabled|consul enabled initContainers|string|false|
