postfix-destination
=========

Configure the postfix SMTPD software to be a final destination for email.

Requirements
------------

No additional requirements are necessary

Role Variables
--------------

my_fqdn: FQDN of the mail server. Defaults to ansible_fqdn
my_domain: DNS Domain of the mail server. Defaults to ansible_domain
my_tls_protocols: List of TLS protocols to allow. Defaults to "!SSLv2, !SSLv3, !TLSv1, !TLSv1.1"
do_ssl: Boolean. Configure a TLS / SSL listener. Defaults to true
do_spam: Configure spamassassin content filtering. Defaults to true
do_inbound_sasl: Allow authentication on _this_ SMTP server
do_outbound_sasl: Allow outbound connections to authenticate to a relay host
outbound_sasl_maps: Mappings of relayhost / username and password combinations
        Array of dicts; dict has following keys:
        - relayhost:
          username:
          password:

Dependencies
------------

There are no external dependencies in this role

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: postfix-destination }

License
-------

GPLv3

Author Information
------------------

Iain M. Conochie <iain@thargoid.co.uk>
