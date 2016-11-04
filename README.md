# Ansible: ssl-certs

Generate and/or deploy SSL certificate

Available on Ansible Galaxy: [pgkehle.ssl-certs](https://galaxy.ansible.com/pgkehle/ssl-certs)

# Examples

## Example to generate a Certificate Signing Request 

```YAML
 - hosts: all
   roles:
     - pgkehle.ssl-certs
       generate_csr: true
       force: true
```

This will create a csr in:

- `~/certs/<fqdn>.csr`


## License

MIT

## Author Information

Paul Kehle  
@pgkehle ([twitter](https://twitter.com/pgkehle), [github](https://github.com/pgkehle), [linkedin](https://www.linkedin.com/in/pgkehle))
