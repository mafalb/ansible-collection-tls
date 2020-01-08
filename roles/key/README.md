# Ansible role - mafalb.tls.key

Role for creating a private TLS key.

### Basic Usage

```ansible
- name: install molecule
  hosts: localhost
  roles:
  - role: mafalb.tls.key
    alias: test.example.com
    key_dir: /tmp/dir
    key_size: 2048
    key_type: RSA
```

## Variables

```key_dir``` the directory where the key is saved

```alias``` the generated key is stored at ```{{ key_dir }}/{{ alias }}.key```

```key_size``` 

```key_type```

## License

GPLv3

