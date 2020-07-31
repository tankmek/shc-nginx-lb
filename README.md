# shc-nginx-loadbalancer

TLS load balancer designed for use in front of a Splunk Search
Head Cluster (SHC). Uses HSTS and the ip_hash load balancing discipline.

## Prerequisites

`policycoreutils-python`  
`openssl`  
`cryptography (pip)`  


```
roles/
└── nginx-lb
├── files
│   └── default.conf
├── handlers
│   └── main.yml
├── README.md
├── tasks
│   ├── config-firewall.yml
│   ├── config-selinux.yml
│   ├── generate-ssl_certs.yml
│   ├── install-repo.yml
│   └── main.yml
├── templates
│   ├── conf.j2
│   └── vhosts.j2
└── vars
└── main.yml
```

## Usage
```
anisble all -m ping

ansible-playbook site.yml
```
