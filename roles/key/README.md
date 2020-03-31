# Ansible role - mafalb.tls.key

|||
|---|---|
|master|![master branch](https://github.com/mafalb/ansible-collection-tls/workflows/CI/badge.svg)|
|dev|![dev branch](https://github.com/mafalb/ansible-collection-tls/workflows/CI/badge.svg?branch=dev)|

Role for creating a private TLS key. For now only RSA keys are supported.

### Basic Usage

```yaml
- hosts: localhost
  roles:
  - role: mafalb.tls.key
    alias: test.example.com-20200114
```

```yaml
- name: distribute to multiple machines
  hosts: node_a
  roles:
  - role: mafalb.tls.key
    alias: test.example.com-20200114
    distribute_to:
    - node_b
    - node_c
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

```key_type``` defaults to RSA, only RSA is implemented for now

---

```key_target_hosts```

```key_target_hosts: "{{ groups['cluster'] }}"```

```yaml
key_target_hosts:
- node_a
- node_b
```

---

## License

GPLv3

