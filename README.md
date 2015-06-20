# fail2ban-filter-apache-fcgi
Filters for fail2ban
Apache fcgi php

##Instructions

1 Upload file to /etc/fail2ban/filter.d
2 Edit your jail.local by adding :

```
[apache-fcgi-botsearch]
enabled = true
port     = http,https
logpath  = %(apache_error_log)s
```

If your fail2ban is installed from distros, have a chance it does not starting the apache filters.
The issue has been fixed in new release of 0.9.2 from (2015/04/29).
Disccused here: https://github.com/fail2ban/fail2ban/issues/959
The solution is to add value backend to the apache files. As this: backend=polling.

## Solves 
### apache-fcgi-botsearch
[Sat Jun 20 02:29:03.262438 2015] [proxy_fcgi:error] [pid 3071:tid 139903794902784] [client 104.151.242.59:55588] AH01071: Got error 'Access to the script '/var/sentora/hostdata/zadmin/public_html/host/wp-login.php/' has been denied (see security.limit_extensions)\n'

[Fri Jun 19 15:28:07.791095 2015] [proxy_fcgi:error] [pid 3071:tid 139903977047808] [client 94.141.43.223:20957] AH01071: Got error 'Unable to open primary script: /var/sentora/hostdata/zadmin/public_html/host/blog1/wp-login.php (No such file or directory)\n'
