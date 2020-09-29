ASBRL-PKI
=========

Generate a KeyPair and a Self-signed certificate.

Requirements
------------
- ssh-keygen
- PyOpenSSL >= 0.15 or cryptography >= 1.6 (if using selfsigned or assertonly provider)
- acme-tiny >= 4.0.0 (if using the acme provider)

Role Variables
--------------

- default_user: 'ubuntu'
- GROUP: "{{default_user}}"
- OWNER: "{{default_user}}"
- MODE: u+r
- DESTINATION_PATH: /home/{{default_user}}/certificates
- KEYPAIR_FILENAME: id_{{KEYPAIR_TYPE}}
- KEYPAIR_TYPE: rsa
- CSR_FILENAME: id_{{KEYPAIR_TYPE}}.csr
- CSR_COMMON_NAME: test
- CRT_FILENAME: id_{{KEYPAIR_TYPE}}.crt
- CRT_PROVIDER: selfsigned
- CRT_SUBJECT: 
      CN: test
- CRT_SELFSIGNED_NOT_AFTER: '' #Default 10 years


Dependencies
------------

The followings ansible modules:
- openssh_keypair
- openssl_csr
- openssl_certificate

Example Playbook
----------------

      - name: Generate Certificate
        include_role:
          name: asbrl-pki
        vars:
          CRT_SELFSIGNED_NOT_AFTER: 20250330202428Z 

License
-------

BSD

Author Information
------------------

Moegui.com