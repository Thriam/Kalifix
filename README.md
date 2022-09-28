# Kalifix
## Fix Kali Linux Wifi/Ethernet connected but no internet access issue
### Execute the following commands in root terminal of your PC

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

# Fix changing time in Windows and Linux
1. Open Regedit as Admin
2. Go to Computer\HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\TimeZoneInformation
3. Right click on Blank Space and select “New > “ & select DWORD(32)Value
4. Rename the newly added value as RealTimeIsUniversal. This is a very important to keep same name.
5. Double click RealTimeIsUniversal & make value data as 1 (from 0). At the end this should be looking like this.
6. Go and sync time in settings
7. Reboot your PC
## We are done. Now you can see both OS will follow UTC time.

# Fix Windows not shown in Kali boot menu
1. Add GRUB_DISABLE_OS_PROBER=false in the grub.cfg file
2. Save the file
### Note:-
### Open file manager as root and then open grub.cfg from there.
## Done

# Create Boot Menu of Windows
1. Right click on "this pc", then click on advanced system settings
2. In Statup and Recovery click on Settings
3. Uncheck "time to display operating systems" and select your main operating system under "default operating system".
4. Click ok, restart your computer and see if it worked.
### Referenced from https://answers.microsoft.com/en-us/windows/forum/all/how-do-i-disable-choose-operating-system/820236bb-925e-4f33-ac93-786e0e43a411
## Done
