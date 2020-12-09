# Disabling ipv6 on a particular interface only

net.ipv6.conf.[interface].disable_ipv6 = [value]
interface – name of the inerface where ipv6 needs to be disabled. For example eth1
value – 0 (enable) or 1 (disable) ipv6 on the interface.

# vi /etc/sysctl.conf
net.ipv6.conf.eth0.disable_ipv6 = 1
sysctl -p
