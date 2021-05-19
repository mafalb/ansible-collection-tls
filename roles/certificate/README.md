# Ansible role - mafalb.tls.certificate

Role for deplying a certificate on a remote machine. There are many files involved. You need the certificate, you need the matching private key and you need the root. Maybe you need the certificate in multiple variations. Some software does expect the certificate and the corresponding private key in separate files, some software expect the certificate and the key in the same file (in pem format). This role does all of that for you.

One question is where does the private key come from. Some have the key centrally managed, the key would be deployed to the target machine.
Another way to do it: create the key on the target machine, with the goal that the key never leaves the target machine(s).

This role supports both ways to do it.
You specify either ```key```, when the key is present on the control node or ```key_alias```, when the key does already exist on the target system.

## Basic Usage with the key already present on the target node

In this case the existing file ```{{ key_dir }}/{{ key_alias }}.key``` is copied to ```{{ key_dir }}/{{ alias }}.key``` (happens on the target node).

```yaml
- hosts: localhost
  roles:
  - role: mafalb.tls.certificate
    alias: test2.example.com
    cert: files/test2.example.com.cert
    key_alias: test2.example.com.key-20200114
    root:
    - files/root.cert
    chain:
    - files/chain1.cert
    - files/chain2.cert
```

## Basic Usage with key present on the control node.

```yaml
- hosts: localhost
  roles:
  - role: mafalb.tls.certificate
    alias: test1.example.com
    cert: files/test1.example.com.cert
    key: test1.example.com
    root:
    - files/root.cert
    chain:
    - files/chain1.cert
    - files/chain2.cert
```

## Variables

```cert``` on the control node: the path to the certificate

```cert_dir``` the directory on the target node where the cert is saved. Operating System dependent default values are provided by the role.

```alias``` resulting file names on the target node are based on this, e.g. the certificate is stored in ```{{ cert_dir }}/{{ alias }}.cert```.`

```key_dir``` the directory where the private key is saved or searched for.

```key_alias``` the key is expected to already exist in the file ```{{ key_dir }}/{{ key_alias }}.key``` and is copied to ```{{ key_dir }}/{{ alias }}.key``` which happens on the key node.

### tls_file_layouts

```yaml
tls_file_layouts:
- singlekey             # cert, key and chain in separate files
- privatepem            # cert, key and chain in one file
- cert+chain            # cert and chain in one file
```

singlekey:

```
/etc/pki/tls/certs/bla.example.com.cert
/etc/pki/tls/certs/bla.example.com.chain.pem
/etc/pki/tls/private/bla.example.com.key
```

privatepem:

```
/etc/pki/tls/private/bla.example.com.pem
```

cert+chain:

```
/etc/pki/tls/certs/bla.example.com.cert+chain.pem
```

## License

GPLv3
