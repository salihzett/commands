# Useful commands

#### for macOS
| Command | Description |
| --- | --- |
| `/usr/libexec/ApplicationFirewall/socketfilterfw --setglobalstate on / off` | enable / disable firewall |
| `/usr/libexec/ApplicationFirewall/socketfilterfw --setstealthmode on / off` | enable / disable stealthmode |
| `defaults write /Library/Preferences/com.apple.alf globalstate -int 0` | To turn firewall off |
| `defaults write /Library/Preferences/com.apple.alf globalstate -int -1` | To turn firewall on for specific applications/services |
| `defaults write /Library/Preferences/com.apple.alf globalstate -int -2` | turn firewall on for network services e.g. DHCP and ipsec, block all the rest |
| `systemsetup -setremotelogin on / off` | enable / disable ssh |
| `spctl --master-enable / disable` | enable / disable gatekeeper |
| `dscl . passwd /Users/admin` | change user (admin) password |
| `dscl . list /Users \| grep -v '_'`  | show user accounts only |
| `ioreg -l \| awk -F\" '/board-id/ { print $4 }'`  | show board id |
| `uname -a` | display kernel version |
| `system_profiler` | display any information |
| `sysctl hw.model \| awk '{ print $2 }'` | display model |
| `system_profiler SPHardwareDataType` | display any information about hardware |
| `system_profiler SPSoftwareDataType ` | display any information about software |
| `system_profiler SPPowerDataType \| grep "Cycle Count" \| awk '{print $3}' ` | display battery cycle count |
| `find / -name "\*filename\*" -print` | search and display file |
| `whoami` | display short username  |
| `id -F` | display full username |
| `osascript -e "long user name of (system info)"` | display full username |
| `/usr/bin/profiles -I -F /tmp/Trust-Profil.mobileconfig` | install profil on macOS |
| `/usr/bin/profiles -L` | list profiles on macOS |
| `/usr/bin/profiles -D` | delete profiles on macOS |
| `echo y \| sudo /usr/bin/profiles -D` | delete profiles on macOS with yes |
| `du -hd 1 /` | display disk usage |
| `df -h` | show space from mounted disk |
| `tmutil disablelocal` | disable local timemachine backups |
| `ln -s /path/to/folder` | create alias |
| `fdesetup sync` | synchronize existing FileVault user information |
| `softwareupdate -l` | search apple software update |
| `softwareupdate -i -a` | install available updates |
| `ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa` | keygen create id_rsa |
| `sudo mdutil -E /` |  reindex volume on the mac |
| `dns-sd -B _ssh._tcp .` | check macs in the network |
| `pwpolicy -a admin -u user -setpolicy "newPasswordRequired=1"` | set newPasswordRequired for user |
| `/usr/libexec/PlistBuddy -c 'Print CFBundleIdentifier' /Applications/foo.app/Contents/Info.plist` | get BundleIdentifier |
| `osascript -e 'id of app "foo" ` | rename volume in efi-menu |
| `sudo bless --folder "volume_path" -label "volume_label"` | get BundleIdentifier |


##### create new admin without admin privilegs
Hold `⌘`+`S` on startup, then
```
/sbin/mount -uw /
rm /var/db/.AppleSetupDone
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

##### create pkg with pkgbuild
```
pkgbuild --root ROOT/ --identifier de.salihzett.test --version 1.0 --nopayload --scripts scripts/ "salihzett.pkg"
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
| `sudo /usr/bin/defaults write /Library/Preferences/ManagedInstalls ClientResourcesFilename -string "foo.zip"` | custom ClientResources |
| `sudo nano /Library/Managed\ Installs/manifests/SelfServeManifest` | current Installs |
| `sudo defaults read /Library/Preferences/ManagedInstalls.plist` | current munki configs |
| `sudo managedsoftwareupdate` | search software and updates via munki |
| `sudo managedsoftwareupdate --installonly` | install available software and updates via munki |
| `sudo managedsoftwareupdate -vvv` | get more verbose output |
| `zip -r site_default.zip resources/ templates/` | zip for munki design |
| `munki://category-all` | overview |
| `munki://updates` | updates |
| `munki://detail-Spotify` | direct to app (detailname) |

#### for Windows OS 
| Command | Description |
| --- | --- |
| `systemreset` | System reset via cmd |
| `systemreset -cleanpc` | FreshStart via cmd|

#### for powershell 
| Command | Description |
| --- | --- |
| `Install-Module -Name AzureAD` | Install module AzureAD |
| `Connect-AzureAD` | Connect to AzureAD |
| `Get-AzureADUser` | Show all AzureAD users |
| `Get-AzureADUser \| Sort-Object DisplayName \| Select-Object DisplayName, UserPrincipalName` | Connect to AzureAD and Sort users |
| `Get-AzureADGroup \| Sort-Object DisplayName \| Select-Object DisplayName, Description` | All groups |
| `Install-Module MSOnline` | Install module Exchange |
| `Connect-MsolService` | Connect to Exchange |
| `Get-MsolUser -All \| select DisplayName, LastPasswordChangeTimeStamp` | Last Password Change time for All Users |
| `Get-MsolUser -All \| select DisplayName, UserPrincipalName, isLicensed` | Display users and isLicensed false true |
| `Get-MsolUser -All \| select DisplayName, UserPrincipalName, isLicensed \| Export-CSV Users.csv -NoTypeInformation` | + export users |
| `Get-Mailbox \| Get-MailboxPermission \| where {$_.user.tostring() -ne "NT AUTHORITY\SELF" -and $_.IsInherited -eq $false}` | Show all shared mailboxes and their members |
| `Get-Mailbox * \| Sort-Object DisplayName \| Select-Object Name, whenMailboxCreated` | Mailbox created date |
| `Set-CalendarProcessing -Identity “Spring” -BookingWindowInDays 1080` | set caleander limit to 1080 days |
| `New-DistributionGroup -Name "Conference Rooms" -OrganizationalUnit "contoso.onmicrosoft.com" -RoomList` | Create a room list |
| `Add-DistributionGroupMember -Identity "Conference Rooms" -Member confroom3223@contoso.com` | add confroom3223 to "Conference Rooms" |
| `Remove-DistributionGroup -Identity <name of group>` | Delete a room list |
| `Get-CASMailbox -Filter {ImapEnabled -eq "true" -or PopEnabled -eq "true" } \| Select-Object @{n = "Identity"; e = {$_.primarysmtpaddress}} \| Set-CASMailbox -PopEnabled $false` | Disable POP |
| `Get-CASMailboxPlan -Filter {ImapEnabled -eq "true" -or PopEnabled -eq "true" } \| set-CASMailboxPlan -PopEnabled $false` | Disable POP for future members |
| `Get-CASMailbox -Filter {ImapEnabled -eq "true" -or PopEnabled -eq "true" } \| Export-CSV EnabledMailServices.csv -NoTypeInformation` | List overview |
| `Get-MsolUser -All \| select DisplayName, LastPasswordChangeTimeStamp` | Last Password Change time for All Users |





#### for aruba switch 
| Command | Description |
| --- | --- |
| `menu` | menu |
| `sh run` | show config |
| `wr mem` | write memory |
| `conf t` | config |
| `sh int br` | overview ports |

#### for unix 
| Command | Description |
| --- | --- |
| `/etc/motd` | welcome screen for ssh connection |
| `/etc/issue` | welcome screen for screen |
| `/etc/gettytab` | banner |
| `smbstatus` | current connections to smb server |
| `/var/log/samba/log.<clientname>` | logs for clients |
| `tail -f /var/log/apache2/access.log` | access log› |



#### for docker 
| Command | Description |
| --- | --- |
| `docker ps -a` | show all container |
| `docker stop $(docker ps -a -q)` |  |
| `docker rm $(docker ps -a -q)` | delete all container (before stop them) |
| `docker images -a` | show all images |
| `docker rmi $(docker images -a -q)` | delete all images |
| `docker build . -t foo` | build image with dockerfile |
| `docker run ` | run image and create container |
| `docker start Container-ID` | start container |
| `docker stop Container-ID` | stop container |
| `docker attach Container-ID` | attach container |
| `docker inspect Container-ID` | render all results in a JSON array |
| `docker inspect Container-ID \| grep -w "IPAddress" \| awk '{ print $2 }' \| head -n 1 \| cut -d "," -f1` | show only ip |

#### for asterisk 
| Command | Description |
| --- | --- |
| `sudo asterisk -vvvvvrx 'core show channels' \| grep call ` | show active calls |
| `sudo asterisk -vvvvvrx 'core show channels verbose'  ` | show active channels |
