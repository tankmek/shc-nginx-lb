# shc-nginx-loadbalancer

TLS load balancer designed for use in front of a Splunk Search
Head Cluster (SHC). Uses HSTS and the ip_hash load balancing discipline.

## Prerequisites

`policycoreutils-python`  
`openssl`  
`cryptography (pip)`  

Assumes RedHat OS family
## Group Variables
```
  ---
  lb:
    user: nginx
    web_port: 80
    ssl_port: 443
    tls_dir: /etc/nginx/ssl
    tls_certificate: lb-cert.crt
    tls_csr: lb-csr.req
    tls_privkey: lb-priv.key
    # With ip-hash, the client’s IP address is used as a hashing
    # key to determine what server in a server group should be
    # selected for the client’s requests. This method ensures that
    # the requests from the same client will always be directed to
    # the same server except when this server is unavailable. 
    load_balance_discipline: ip_hash
```

## Role Variables




## Project Contents
```
shc-nginx-lb/
├── ansible.cfg
├── group_vars
│   └── lb
│       └── vars.yml
├── inventory
├── playbooks
│   └── config-lb.yml
├── README.md
├── roles
│   └── nginx-lb
│       ├── files
│       │   └── default.conf
│       ├── handlers
│       │   └── main.yml
│       ├── README.md
│       ├── tasks
│       │   ├── config-firewall.yml
│       │   ├── config-selinux.yml
│       │   ├── generate-ssl_certs.yml
│       │   ├── install-repo.yml
│       │   └── main.yml
│       ├── templates
│       │   ├── conf.j2
│       │   └── vhosts.j2
│       └── vars
│           └── main.yml
└── site.yml

```

## Usage
```
anisble all -m ping

ansible-playbook site.yml
```
