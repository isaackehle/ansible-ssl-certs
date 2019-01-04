# Ansible Role - ssl-certs

Generate and/or deploy SSL certificate

Available on Ansible Galaxy: [pgkehle.ssl-certs](https://galaxy.ansible.com/pgkehle/ssl-certs)

## Input and Variables

```yaml
flags:
  force:                set to true to force any of the previous actions
  client_config:        set to true to ensure the proper SSL settings for generating a client certificate
  create_csr:           set to true to generate a new CSR on a remote machine
  pull_csr:             set to true to copy CSR local
  deploy:               set to true to deploy certificates
  create_ssc:           set to true to create a Self Signed Certificate
  dh_param:             set to true to generate a dhparam file

cert_config:
  country:              Country for the cert
  locality:             Locality for the cert
  state:                State for the cert
  organization:         Organization for the cert
  ou:                   Organizational Unit for the cert
  cn:                   Common name for the cert, usually fqdn
  dc:                   Domain Component for the cert, if any
  email:                Email for the cert
  subject:              Subject for the cert
```

## Examples

### Example to generate a Certificate Signing Request

```yaml
- hosts: all
  gather_facts: "{{ ansible_host != 'localhost' }}"
  vars:
    flags:
      - client_config
      - force
      - create_csr
  roles:
    - { role: pgkehle.ssl-certs }
```

## Example to move a certificate into place

```yaml
- hosts: all
  gather_facts: "{{ ansible_host != 'localhost' }}"
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
