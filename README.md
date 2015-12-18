ansible-ntpd
============

Install and configure ntpd on rhel and debian hosts hosts. This is only
suitable for client-server mode.

Requirements
------------

None.

Role Variables
--------------

The variables that can be passed to this role and a brief description about
them are as follows. See the NTP configuration documentation for details:

```yaml
# The 0, 1, 2 and 3.pool.ntp.org names point to a random set of servers that
# will change every hour. See http://www.pool.ntp.org/en/use.html
ntpd_sources:
  - 0.ca.pool.ntp.org
  - 1.ca.pool.ntp.org
  - 2.ca.pool.ntp.org
  - 3.ca.pool.ntp.org

# By default, hosts on local network are less restricted.
# Override this for more specifics needs
ntpd_restrict:
  - restrict 10.0.0.0 mask 255.0.0.0 nomodify notrap nopeer
  - restrict 192.168.0.0 mask 255.255.0.0 nomodify notrap nopeer
  - restrict 172.16.0.0 mask 255.240.0.0 nomodify notrap nopeer

# undefined crypto settings
ntpd_crypto: ''
ntpd_includefile: ''
ntpd_keys: ''
ntpd_trustedkey: ''
ntpd_requestkey: ''
ntpd_controlkey: ''
```

See templates/ntp.conf.j2 for other defaults.

Examples
--------

Install ntp and set the default settings.

```yaml
  - hosts: all
    roles:
      - role: ntpd
```

Dependencies
------------

None

License
-------

MIT

Author Information
------------------

Felix Archambault
