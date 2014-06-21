openbsd-comcast-ipv6
====================

Simple recipe for using an OpenBSD router on for native ipv6 on Comcast (tested in Washington, DC). Does not include any `pf` modifications you may need to make for your ruleset.

* Install wide-dhcpv6:

```
sudo pkg_add -rv ftp://ftp.openbsd.org/pub/OpenBSD/`uname -r`/packages/`uname -p`/wide-dhcpv6
```

* Load up the configuration files/snippets included within this repository, replacing EXTIF and INTIF with the appropriate real interface names. You can duplicate the INTIF sections/snippets if you have multiple internal subnets you wish to route/provide ipv6 for.

* Save local gateway:

```
netstat -rn | awk '/default/ && /:/ { print $2}' | sudo tee -a /etc/mygate
```

* Reboot

```
sudo shutdown -r now
```
