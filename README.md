# slackware-tales
Some slackware scripts, utils, howtos

## 1. disk encryption and boot

- https://www.tumfatig.net/2023/install-slackware-linux-with-full-disk-ecryption-on-a-uefi-system/
- https://wiki.archlinux.org/title/EFI_system_partition#GPT_partitioned_disks
- https://blog.aktsbot.in/slackware-install-lvm-luks.html
- https://docs.slackware.com/slackbook:booting
- https://docs.slackware.com/howtos:slackware:kernel_huge_for_generic (optional, just wizard)

### my way

- Go for ELILO (UEFI) via the wizard.
- If cannot boot [check this](https://www.linuxquestions.org/questions/slackware-installation-40/elilo-boot-entry-not-being-configured-4175663976/#post6056260).
- When encrypted swap is present [enable hibernate](https://wiki.archlinux.org/title/Power_management/Suspend_and_hibernate) for less power consumption

## 2. packages

I don't want to add an entire package manager yet so I write two small scripts to deal with most of [slackware builds](https://slackbuilds.org/) I need.

luser = non-root

1. As luser, add slackbuilds key to https://slackbuilds.org/faq/#gpg.
2. Add these scripts on /usr/local/bin or **better** read it and write something similar yourself

| #  || Run as          | |
|---|---|--------------|---|
| 1 | chirale_slackbuilds | luser  | Download from slackbuilds FTP, check via gpg, unpack it and download the related software third-party as in DOWNLOAD... variables of slackbuild .info file.  |
| 2 | chirale_slackbuilds_install | root  | Create .tgz package for installpkg.  |

Then:

1. Visit https://slackbuilds.org/repository/
2. Find the slackbuild you need
3. Reconstruct the dependencies (you have to install these first) and install with slackbuilds or other method (e.g. building from source)
4. As luser, run command (1) using command games jg-picodrive to download https://slackbuilds.org/repository/15.0/games/jg-picodrive/ (your slackware version e.g. 15.0 will be auto-detected). If you encounter an error, do manually the needed steps, usually to download the third-party software.
5. As root, run command (2) using command jg-picodrive.
6. Go to /usr/local/etc then run installpkg LONGNAMEHERE.tgz
7. You can uninstall with removepkg jg-picodrive
