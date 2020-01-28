# Ansible role - mafalb.tls.csr

Role for creating a CSR

### Basic Usage

```yaml
- name: csr with preexisting key
  hosts: localhost
  roles:
  - role: mafalb.tls.csr
    key_file: test.example.com-20200114.key
    alias: test.example.com
    x509_cn: test.example.com
    x509_organization: bla
    x509_locality: Vienna
    x509_province: Vienna
    x509_country: AT
```

```yaml
- name: csr with no preexisting key
  hosts: localhost
  roles:
  - role: mafalb.tls.key
    alias: test.example.com-20200114    
  - role: mafalb.tls.csr
    key_file: test.example.com-20200114.key
    alias: test.example.com
    x509_cn: test.example.com
    x509_organization: bla
    x509_locality: Vienna
    x509_province: Vienna
    x509_country: AT
```

## Variables

---

```csr_dir```

The directory where the csr and it's config is saved. Defaults to system specific value, e.g. /etc/pki/tls/certs on RedHat.

---

```alias```

The generated CSR is stored at ```{{ csr_dir }}/{{ alias }}.csr```. Required.

---

```key_file```

The private key used relative to ```key_dir```, but it is possible to specify an absolute path.

---

```csr_overwrite```

The CSR will is regenerated even if it already exists.

---

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
