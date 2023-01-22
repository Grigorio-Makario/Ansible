Как запретить systemd-resolved использовать порт 53 в Ubuntu

nano /etc/systemd/resolved.conf

[Resolve]
DNS=8.8.8.8
#FallbackDNS=
#Domains=
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
#DNSOverTLS=no
#Cache=no
DNSStubListener=no
#ReadEtcHosts=yes

ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf

reboot

lsof -i :53
