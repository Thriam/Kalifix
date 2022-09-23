# Kalifix
## Fix Kali Linux Wifi/Ethernet connected but no internet access issue

┌──(root㉿kali)-[~]
└─# ping google.com
ping: google.com: Temporary failure in name resolution
                                                                             
┌──(root㉿kali)-[~]
└─# systemctl enable systemd-networkd
Created symlink /etc/systemd/system/dbus-org.freedesktop.network1.service → /lib/systemd/system/systemd-networkd.service.
Created symlink /etc/systemd/system/multi-user.target.wants/systemd-networkd.service → /lib/systemd/system/systemd-networkd.service.
Created symlink /etc/systemd/system/sockets.target.wants/systemd-networkd.socket → /lib/systemd/system/systemd-networkd.socket.
Created symlink /etc/systemd/system/sysinit.target.wants/systemd-network-generator.service → /lib/systemd/system/systemd-network-generator.service.
Created symlink /etc/systemd/system/network-online.target.wants/systemd-networkd-wait-online.service → /lib/systemd/system/systemd-networkd-wait-online.service.
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# systemctl enable systemd-resolved
Created symlink /etc/systemd/system/dbus-org.freedesktop.resolve1.service → /lib/systemd/system/systemd-resolved.service.
Created symlink /etc/systemd/system/multi-user.target.wants/systemd-resolved.service → /lib/systemd/system/systemd-resolved.service.
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# systemctl start systemd-networkd
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# systemctl start systemd-resolved
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# ln -sf /run/systemd/resolve/resolve.conf /etc/resolv.conf
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# service resolvconf restart      
Failed to restart resolvconf.service: Unit resolvconf.service not found.
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf 
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# service resolvconf restart                              
Failed to restart resolvconf.service: Unit resolvconf.service not found.
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# service resolv.conf restart
Failed to restart resolv.conf.service: Unit resolv.conf.service not found.
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# service network-manager restart
Failed to restart network-manager.service: Unit network-manager.service not found.
                                                                                                                                                                                                                                            
┌──(root㉿kali)-[~]
└─# ping google.com
PING google.com(maa05s10-in-x0e.1e100.net (2404:6800:4007:808::200e)) 56 data bytes

## Finally restart your PC (recommended)
