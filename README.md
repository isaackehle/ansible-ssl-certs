# Ansible Role - ssl-certs

Generate and/or deploy SSL certificate

Available on Ansible Galaxy: [isaackehle.ssl-certs](https://galaxy.ansible.com/isaackehle/ssl-certs)

## Input and Variables

```yaml
flags:
  force: set to true to force any of the previous actions
  client_config: set to true to ensure the proper SSL settings for generating a client certificate
  create_csr: set to true to generate a new CSR on a remote machine
  pull_csr: set to true to copy CSR local
  deploy: set to true to deploy certificates
  create_ssc: set to true to create a Self Signed Certificate
  dh_param: set to true to generate a dhparam file

cert_config:
  country: Country
  locality: Locality
  state: State
  organization: Organization
  ou: Organizational Unit
  cn: Common name, usually fqdn
  dc: Domain Component, if any
  email: Email
  subject: Subject
```

## Examples

### Example to generate a Certificate Signing Request

```yaml
- hosts: all
  gather_facts: inventory_hostname != 'localhost'
  vars:
    flags:
      - client_config
      - force
      - create_csr
  roles:
    - { role: isaackehle.ssl-certs }
```

## Example to move a certificate into place

```yaml
- hosts: all
  gather_facts: inventory_hostname != 'localhost'
  vars:
    flags:
      - deploy
  roles:
    - isaackehle.ssl-certs
```

## Linting

```bash
yamllint -c yamllint.yaml .
ansible-lint .
```

## License

MIT

## Author Information

Isaac Kehle
@isaackehle ([twitter](https://twitter.com/isaackehle), [github](https://github.com/isaackehle), [linkedin](https://www.linkedin.com/in/isaackehle))
