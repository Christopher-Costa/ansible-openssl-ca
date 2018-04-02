Ansible Role: ansible-openssl-ca
=========

An Ansible Role to install OpenSSL root and intermediate Certificate Authorities for managing your own certificates..

Requirements
------------

* Ansible 2.5. Backward compatibility with older versions of Ansible is not guaranteed.
* A target system running RHEL/CentOS 7 with access to the default yum repositories.

Role Variables
--------------

The role requires several variables representing attributes of the Distinguished Name for the CA certificates.  With exception of the CN, the certificates are assumed to have common attributes.

    cert_C:
    cert_ST:
    cert_L:
    cert_O:
    cert_OU:

    root_cert_CN:
    int_cert_CN:

Variable are used to identify the directory path for the ca files.   The default settings will place files in /root/ca/root and /root/ca/intermediate accordingly.

    ca_dir: /root/ca
    ca_root_dir: root
    ca_int_dir: intermediate

Other variables are used to identify other certificate attributes.

    crypto_hash: sha256
    days_valid: 7300
    key_length: 2048

Other variables are used to name the various private key, certificate signing request, and certificate files.

    root_key: ca.key.pem
    root_cert: ca.cert.pem

    int_key: intermediate.key.pem
    int_csr: intermediate.csr.pem
    int_cert: intermediate.cert.pem

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: ca-servers
      roles:
        - role: openssl_ca
          vars:
            ca_dir: /home/ca

License
-------

MIT

Author Information
------------------

Christopher Costa, christopher.costa@gmail.com
