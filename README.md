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



