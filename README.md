# Ansible: ssl-certs

Generate and/or deploy SSL certificate

Available on Ansible Galaxy: [pgkehle.ssl-certs](https://galaxy.ansible.com/pgkehle/ssl-certs)

# Input and Variables

```
flags:
    force               set to true to force any of the previous actions
    client_config       set to true to ensure the proper SSL settings for generating a client certificate
    csr_create          set to true to generate a new CSR on a remote machine
    csr_pull            set to true to copy CSR local
    deploy              set to true to deploy certificates
    ssc_generate        set to true to create a Self Signed Certificate
    dh_param            set to true to generate a dhparam file

certs_path              Local path for cert CSR/signed cert storage

sc_country              Country for the cert                        
sc_locality             Locality for the cert
sc_state                State for the cert
sc_organization         Organization for the cert
sc_ou                   Organizational Unit for the cert
sc_email                Email for the cert
sc_common_name          Common name for the cert, usually fqdn
sc_domain_comp          Domain Component for the cert, if any
```

## Examples

### Example to generate a Certificate Signing Request 

```YAML
- hosts: all
  gather_facts: "{{ansible_host != 'localhost'}}"
  vars: 
    flags:
      - client_config
      - force
      - csr_create
  roles:
    - { role: pgkehle.ssl-certs }
```

## Example to move a certificate into place 

```YAML
- hosts: all
  gather_facts: "{{ansible_host != 'localhost'}}"
  vars: 
    flags:
      - deploy
  roles:
    - pgkehle.ssl-certs
```

## License

MIT

## Author Information

Paul Kehle  
@pgkehle ([twitter](https://twitter.com/pgkehle), [github](https://github.com/pgkehle), [linkedin](https://www.linkedin.com/in/pgkehle))

## For local development testing

```bash
rsync -av --delete ~/code/ansible-ssl-certs/* ~/.ansible/roles/pgkehle.ssl-certs
```

