postfix-destination
=========

Configure the postfix SMTPD software to be a final destination for email.

Requirements
------------

No additional requirements are necessary

Role Variables
--------------

my_fqdn:          FQDN of the mail server. Defaults to ansible_fqdn
my_domain:        DNS Domain of the mail server. Defaults to ansible_domain
my_tls_protocols: List of TLS protocols to allow. Defaults to "!SSLv2, !SSLv3, !TLSv1, !TLSv1.1"
key_file:         Name of the TLS key file. Defaults to my_fqdn.pem
cert_file:        Name of the TLS certificate file. Defaults to my_fqdn.crt
do_ssl:           Boolean. Configure a TLS / SSL listener. Defaults to true
do_spam:          Boolean.Configure spamassassin content filtering. Defaults to true
do_inbound_sasl:  Boolean. Allow authentication on _this_ SMTP server. Defaults to true.

outbound_sasl_maps: Mappings of relayhost / username and password combinations
        to authenticate with remote SMTP hosts. Array of dicts; dict has following keys:
        - relayhost:
          username:
          password:

The following variables are *required* for LDAP configuration.

do_ldap:          Boolean. Configure postfix to use LDAP storage for virtual alias domains.
domain:           Base domain for the LDAP server.
admin_rdn:        RDN of the LDAP admin user.
admin_password:   Password for the admin user.


Dependencies
------------

This role requires the python-ldap module installed on the control machine.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: postfix-destination,
             outbound_sasl_maps:
               - relayhost: smtp.example.com
                 username: relay@example.com
                 password: secureisitnot? }

License
-------

GPLv3

Author Information
------------------

Iain M. Conochie <iain@thargoid.co.uk>
