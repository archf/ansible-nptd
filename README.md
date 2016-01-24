ansible-ntpd
============

Install and configure ntpd on rhel and debian hosts. This is only
suitable for client-server mode.

Target can either be a ntpd server or a ntpd client.

Requirements
------------

None.

Role Variables
--------------

Here are the variables as well as the defaults:

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

# no stats logging
ntpd_log_stats: no

# undefined crypto settings
ntpd_crypto: ''
ntpd_includefile: ''
ntpd_keys: ''
ntpd_trustedkey: ''
ntpd_requestkey: ''
ntpd_controlkey: ''
```

Settings above work well for simple ntp clients.

See templates/ntp.conf.j2 for other defaults.

Examples
--------

Install ntp and set the default settings.

```yaml
  - hosts: all
    roles:
      - role: archf.ntpd
```

Dependencies
------------

None

Todo
-----

- add peer support
- improve statistics configuration

License
-------

BSD

Author Information
------------------

Felix Archambault
