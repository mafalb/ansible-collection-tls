# Ansible role - mafalb.tls.key

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

```one_key_for_all``` boolean, defaults to False

```yaml
one_key_for_all: true
```

Use this if you want the same key on all hosts in the play, e.g. if you have a cluster.

---

## License

GPLv3

