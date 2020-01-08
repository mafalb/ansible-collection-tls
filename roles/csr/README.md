# Ansible role - mafalb.tls.csr

Role for creating a CSR

### Basic Usage

```ansible
- hosts: localhost
  roles:
  - role: mafalb.tls.csr
    csr_dir: /tmp/dir
    alias: test.example.com
    key_file: /tmp/dir/test.example.com.key
    x509_cn: test.example.com
    x509_organization: bla
    x509_locality: Vienna
    x509_province: Vienna
    x509_country: AT
    x509_sans:
    - example.com

   
```

## Variables

```csr_dir``` the directory where the key is saved

```alias``` the generated CSR is stored at ```{{ csr_dir }}/{{ alias }}.csr```

```key_file``` the private key used

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

