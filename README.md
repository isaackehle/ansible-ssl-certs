# Ansible: ssl-certs

Generate and/or deploy SSL certificate

Available on Ansible Galaxy: [pgkehle.ssl-certs](https://galaxy.ansible.com/pgkehle/ssl-certs)

# Input and Variables

```
generate_csr            set to true to generate a new CSR
pull_csr                set to true to copy CSR local
do_client_config        set to true to ensure the proper SSL settings for generating a client certificate
generate_ssc            set to true to create a Self Signed Certificate
generate_dh_param       set to true to generate a dhparam file
force                   set to true to force any of the previous actions

sc_local_path           Local path for cert CSR/signed cert storage

sc_country              Country for the cert                        
sc_locality             Locality for the cert
sc_state                State for the cert
sc_organization         Organization for the cert
sc_ou                   Organizational Unit for the cert
sc_email                Email for the cert
sc_common_name          Common name for the cert, usually fqdn
sc_domain_comp          Domain Component for the cert, if any
```

# Examples

## Example to generate a Certificate Signing Request 

```YAML
 - hosts: all
   roles:
     - pgkehle.ssl-certs
       generate_csr: true
       do_client_config: true
       force: true
```

## Example to move a certificate into place 

```YAML
 - hosts: all
   roles:
     - pgkehle.ssl-certs
       deploy_cert: true
```



## License

MIT

## Author Information

Paul Kehle  
@pgkehle ([twitter](https://twitter.com/pgkehle), [github](https://github.com/pgkehle), [linkedin](https://www.linkedin.com/in/pgkehle))
