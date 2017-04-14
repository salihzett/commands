# Useful commands

#### for macOS
| Command | Description |
| --- | --- |
| `/usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on / off` | enable / disable firewall |
| `/usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode on / off` | enable / disable stealthmode |
| `systemsetup -setremotelogin on / off` | enable / disable ssh |
| `spctl --master-enable / disable` | enable / disable gatekeeper |
| `dscl . passwd /Users/admin` | change user (admin) password |
| `dscl . list /Users | grep -v '_'` | show user accounts only |
| `uname -a` | display kernel version |
| `sysctl hw.model | awk '{ print $2 }'` | display model |
| `system_profiler` | display any information |
| `sysctl hw.model | awk '{ print $2 }'` | display model |
| `system_profiler SPHardwareDataType` | display any information about hardware |
| `system_profiler SPSoftwareDataType ` | display any information about software |
| `find / -name "\*filename\*" -print` | search and display file |
| `whoami` | display short username  |
| `id -F` | display full username |
| `osascript -e "long user name of (system info)"` | display full username |
| `/usr/bin/profiles -I -F /tmp/Trust-Profil.mobileconfig` | install profil on macOS |
| `/usr/bin/profiles -L` | list profiles on macOS |
| `/usr/bin/profiles -D` | delete profiles on macOS |
| `echo y \| sudo /usr/bin/profiles -D` | delete profiles on macOS with yes |
| `du -hd 1 /` | display disk usage |
| `tmutil disablelocal` | disable local timemachine backups |
| `softwareupdate -l` | search apple software update |
| `softwareupdate -i -a` | install available updates |
| `ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa` | keygen create id_rsa |
| `sudo mdutil -E /` |  reindex volume on the mac |



##### create new admin without admin privilegs
Hold `⌘`+`S` on startup, then
```
/sbin/mount -uw /
rm /var/db/.applesetupdone
reboot
```

##### config remote host with id_rsa.pub
```
scp ~/.ssh/id_rsa.pub <user>@<remote_host>:
mkdir ~/.ssh
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
rm ~/id_rsa.pub
chmod 600 ~/.ssh/authorized_keys
```

##### install pkg on remote host
```
scp /PATHTO/<file>.pkg <user>@<remote_host>:/tmp/
sudo installer -pkg /tmp/<file>.pkg -target /
```

#### for munki 
| Command | Description |
| --- | --- |
| `sudo defaults write /Library/Preferences/ManagedInstalls InstallAppleSoftwareUpdates -bool True / False` | enable / disable Apple Updates via Munki |
| `sudo /usr/bin/defaults write /Library/Preferences/ManagedInstalls DaysBetweenNotifications -int -1` | notification interval |
| `sudo nano /Library/Managed\ Installs/manifests/SelfServeManifest` | current Installs |
| `sudo managedsoftwareupdate` | search software and updates via munki |
| `sudo managedsoftwareupdate --installonly` | install available software and updates via munki |
| `sudo managedsoftwareupdate -vvv` | get more verbose output |
| `munki://category-all.html` | overview |
| `munki://updates.htm` | updates |
| `munki://detail-Spotify` | direct to app (detailname) |

#### for unix 
| Command | Description |
| --- | --- |
| `/etc/motd` | welcome screen for ssh connection |
| `/etc/issue` | welcome screen for screen |
| `/etc/gettytab` | banner |
| `smbstatus` | current connections to smb server |



