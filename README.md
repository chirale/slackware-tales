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

## 2. Packages

I don't want to add an entire package manager yet so I write two small scripts to deal with most of [slackware builds](https://slackbuilds.org/) I need.

luser = non-root

1. As luser, add slackbuilds key to https://slackbuilds.org/faq/#gpg.
2. Add these scripts on /usr/local/bin or **better** read and write something similar yourself

|              |   |   |   |   |
|--------------|---|---|---|---|
| Run as luser  | Download from slackbuilds FTP, check via gpg, unpack.  |   |   |   |
| Run as root  | Create .tgz package for installpkg.  |   |   |   |
|              |   |   |   |   |
