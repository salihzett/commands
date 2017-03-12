# Useful commands

#### for macOS
| Command | Description |
| --- | --- |
| `/usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on / off` | enable / disable firewall |
| `/usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode on / off` | enable / disable stealthmode |
| `systemsetup -setremotelogin on / off` | enable / disable ssh |
| `spctl --master-enable / disable` | enable / disable gatekeeper |
| `dscl . passwd /Users/admin` | change user (admin) password |
| `uname -a` | display kernel version |
| `system_profiler` | display any information |
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
| `ssh-keygen -t rsa -b 4096 -f ~..ssh/id_rsa` | keygen create id_rsa |


##### create new admin without admin privilegs
Hold `⌘`+`S` on startup, then
```
/sbin/mount -uw /
rm /var/db/.applesetupdone
reboot
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
