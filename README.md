| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| aws\_account\_id | AWS account ID | `string` | n/a | yes |
| aws\_dynamodb\_read\_write\_capacity | AWS dynamodb read/write capacity for provisioning service tables | <pre>object({<br>    table_service_template = object({<br>      read  = number<br>      write = number<br>    })<br>    table_release = object({<br>      read  = number<br>      write = number<br>    })<br>    table_openshift_template = object({<br>      read  = number<br>      write = number<br>    })<br>  })</pre> | <pre>{<br>  "table_openshift_template": {<br>    "read": 10,<br>    "write": 10<br>  },<br>  "table_release": {<br>    "read": 10,<br>    "write": 10<br>  },<br>  "table_service_template": {<br>    "read": 10,<br>    "write": 10<br>  }<br>}</pre> | no |
| aws\_dynamodb\_url | AWS dynamodb URL | `string` | n/a | yes |
| aws\_rds | AWS RDS instance information for provisioning service to manage RDS instances | <pre>object({<br>    url                    = string<br>    master_username        = string<br>    subgroup_name          = string<br>    vpc_security_group_ids = list(string)<br>  })</pre> | n/a | yes |
| aws\_rds\_config | AWS RDS database configuration | <pre>object({<br>    database_name  = string<br>    engine_version = string<br>    instance_class = string<br>  })</pre> | <pre>{<br>  "database_name": "postgres",<br>  "engine_version": "11.latest",<br>  "instance_class": "db.t2.large"<br>}</pre> | no |
| cluster | Cluster information in which provisioning service is deployed into | <pre>object({<br>    url             = string<br>    name_prefix     = string<br>    route_id_prefix = string<br>  })</pre> | n/a | yes |
| cms\_url | The URL for Client Management Service | `string` | n/a | yes |
| database | Database information for provisioning service. URL includes port | <pre>object({<br>    url      = string<br>    name     = string<br>    username = string<br>  })</pre> | n/a | yes |
| database\_hikari | Hikari minimum idle and maximum pool size for database | <pre>object({<br>    min_idle     = number<br>    max_poolsize = number<br>  })</pre> | <pre>{<br>  "max_poolsize": 10,<br>  "min_idle": 1<br>}</pre> | no |
| docker\_email | Docker email | `string` | `"serviceaccount"` | no |
| docker\_name | Docker name | `string` | `"da-saas-docker-repo"` | no |
| docker\_registry | Docker Registry | `string` | n/a | yes |
| docker\_username | Docker username | `string` | `"serviceaccount"` | no |
| ingress\_enabled | Determines if ingress is enabled for provisioning service or not | `bool` | `true` | no |
| kafka | Kafka details for provisioning service | <pre>object({<br>    default_server            = string<br>    bps_server                = string<br>    server                    = string<br>    trusted_installation_urls = list(string)<br>  })</pre> | n/a | yes |
| livenessProbe\_enabled | Determines whether liveness probe is enabled for provisioning service or not | `bool` | `true` | no |
| persona\_persistence | Persona Persistence for read and write | <pre>object({<br>    read  = string<br>    write = string<br>  })</pre> | <pre>{<br>  "read": "DYNAMO_DB",<br>  "write": "DYNAMO_DB"<br>}</pre> | no |
| provisioning\_service\_image\_repository | Docker image repository for provisioning service | `string` | n/a | yes |
| provisioning\_service\_image\_sha | Docker image sha for provisioning service | `string` | n/a | yes |
| provisioning\_service\_image\_tag | Docker image tag for provisioning service | `string` | n/a | yes |
| proxy | proxy for provisioning service. Only required if proxy is enabled | <pre>object({<br>    enabled  = bool<br>    http     = string<br>    https    = string<br>    no_proxy = string<br>  })</pre> | <pre>{<br>  "enabled": false,<br>  "http": "",<br>  "https": "",<br>  "no_proxy": ""<br>}</pre> | no |
| readinessProbe\_enabled | Determines whether readiness probe is enabled for provisioning service or not | `bool` | `true` | no |
| redis | Redis details for provisioning service | <pre>object({<br>    server       = string<br>    token_server = string<br>  })</pre> | n/a | yes |
| region | The cloud region in which the provisioning service will be deployed into | `string` | n/a | yes |
| replica\_count | The number of instances to be deployed for provisioning service | `string` | `"1"` | no |
| servicegroup\_owners | owners of the service group | `list(string)` | n/a | yes |
| splunk | Splunk for provisioning service. Details are required only if splunk is enabled | <pre>object({<br>    enabled = bool<br>    url     = string<br>    hec     = string<br>    ca_cert = string<br>  })</pre> | <pre>{<br>  "ca_cert": "",<br>  "enabled": false,<br>  "hec": "",<br>  "url": ""<br>}</pre> | no |
| stack | Provisioning service stack | `string` | n/a | yes |
| vault | Vault details for provisioning service | <pre>object({<br>    token          = string<br>    pki_dns_suffix = string<br>    address        = string<br>    pki = object({<br>      role                        = string<br>      common_name                 = string<br>      renewal_internal_in_minutes = number<br>    })<br>  })</pre> | n/a | yes |
