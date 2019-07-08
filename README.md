# ProxySQL cPanel Hook #

Automatically manages ProxySQL mysql_users table for WHM & cPanel events.

## Installation Steps ##

1) Save the file into one of these locations on the WHM/cPanel server:
  - /usr/local/cpanel
  - /usr/local/cpanel/3rdparty/perl/514/lib64/perl5/cpanel_lib/x86_64-linux-64int
  - /usr/local/cpanel/3rdparty/perl/514/lib64/perl5/cpanel_lib
  - /usr/local/cpanel/3rdparty/perl/514/lib64/perl5/5.14.4/x86_64-linux-64int
  - /usr/local/cpanel/3rdparty/perl/514/lib64/perl5/5.14.4
  - /opt/cpanel/perl5/514/site_lib/x86_64-linux-64int
  - /opt/cpanel/perl5/514/site_lib
  - /var/cpanel/perl5/lib

2) Update the ProxySQL admin credentials (line 16 to 19):

```perl
my $proxysql_admin_host = '192.168.0.16';
my $proxysql_admin_port = '6032';
my $proxysql_admin_user = 'proxysql-admin';
my $proxysql_admin_pass = 'mys3cr3t';
```

** If the ProxySQL writer hostgroup ID is not 10, you might need to change the ``$proxysql_default_hostgroup`` variable (line 22) accordingly.

3) Register with cPanel hook system:

```bash
/usr/local/cpanel/bin/manage_hooks add module ProxysqlHook
```

4) You're all set.

## Example Implementation ##

Check out this blog post, [MySQL Replication with ProxySQL on WHM/cPanel Servers](https://severalnines.com/blog/mysql-replication-proxysql-whmcpanel-servers-part-1) on how to use this hook to achieve a highly available MySQL service on WHM/cPanel server.

** Tested on WHM/cPanel 80.0 (build 18), MySQL 5.7.26, ProxySQL 1.4.14, CentOS 7.6.1810
