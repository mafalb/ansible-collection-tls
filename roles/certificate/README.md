# Ansible role - mafalb.tls.certificate

Role for copying a certificate to a remote machine 

### Basic Usage

```ansible
- hosts: localhost
  roles:
  - role: mafalb.tls.certificate
    alias: test1.example.com
    cert: files/test1.example.com.cert
    key: files/test1.example.com.key
    root: files/root.cert
    chain:
    - files/chain1.cert
    - files/chain2.cert

- hosts: localhost
  roles:
  - role: mafalb.tls.certificate
    alias: test2.example.com
    cert: files/test2.example.com.cert
    remote_key: test2.example.com.key-20200114
    root: files/root.cert
    chain:
    - files/chain1.cert
    - files/chain2.cert

   
```

## Variables

```cert``` the local path to the certificate

```cert_dir``` the directory where the cert is saved

```alias``` the generated CSR is stored at ```{{ csr_dir }}/{{ alias }}.csr```

```key_dir``` the directory where the key is saved

```csr_overwrite```

## Variables for certificate Information

```x509_cn```
```x509_organization```
```x509_locality```
```x509_province```
```x509_country```

```yaml
x509_sans:
- example.com
```

```yaml
x509_extended_key_usage:
- serverAuth
- clientAuth
- ...
```

## License

GPLv3
