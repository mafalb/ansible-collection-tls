# Ansible role - mafalb.tls.key

Role for creating a private TLS key. For now only RSA keys are supported.

### Basic Usage

```yaml
- hosts: localhost
  roles:
  - role: mafalb.tls.key
    alias: test.example.com-20200114
```

## Variables

---

```key_dir```

The directory where the key is saved.
Defaults to system specific value, e.g. ```/etc/pki/tls/private``` on RedHat.

---

```alias```

the generated key is stored at ```{{ key_dir }}/{{ alias }}.key```
you can specify alias with subdirectories, e.g.

```yaml
alias: subdirectory/test.example.com
```

will save the key into ```{{ key_dir}}/subdirectory/test.example.com.key```

---

```key_size```

---

```key_type``` defaults to RSA

---


## License

GPLv3

