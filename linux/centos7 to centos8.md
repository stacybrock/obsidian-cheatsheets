# Upgrading CentOS 7 to CentOS 8
Use `vault.centos.org` because CentOS 7 is no longer supported.
```
# sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
# sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```
Install `rpmconf`.
```
# yum install rpmconf epel-release yum-utils
# rpmconf -a
```
Say "N" to each prompt, to keep current configs.

List unneeded and duplicate packages, and remove them.
```
# package-cleanup --leaves > to_remove.txt
# package-cleanup --orphans >> to_remove.txt

#!/usr/bin/env bash

while IFS= read -r package; do
    yum remove -y "$package"
done < to_remove.txt
```

Install `dnf`.
```
# yum install dnf
```
Remove `yum`.
```
# dnf remove -y yum yum-metadata-parser
# rm -Rf /etc/yum
```
Build cache for dnf repositories.
```
# dnf -y makecache
```
Upgrade to latest packages.
```
# dnf upgrade
```
Clean cache and download packages.
```
# dnf clean all
```
Install `centos-release` and `epel-release` from CentOS 8.
```
# dnf install http://vault.centos.org/centos/8/BaseOS/x86_64/os/Packages/{centos-linux-repos-8-3.el8.noarch.rpm,centos-linux-release-8.5-1.2111.el8.noarch.rpm,centos-gpg-keys-8-3.el8.noarch.rpm}

# dnf -y upgrade https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
```
Clean cache and download packages one more time.
```
# dnf clean all
```
Remove old kernels.
```
# rpm -e `rpm -q kernel`
# rpm -e --nodeps sysvinit-tools
```
Update repo configs to use `vault.centos.org` one more time because we've added repos for CentOS 8.
```
# sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
# sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```
Run `distro-sync`.
```
# dnf --releasever=8 --allowerasing --setopt=deltarpm=false distro-sync
```
Resolve dependency errors.
```
Running transaction check
Error: transaction check vs depsolve:
(gcc >= 8 with gcc < 9) is needed by annobin-9.72-1.el8_5.2.x86_64
rpmlib(RichDependencies) <= 4.12.0-1 is needed by annobin-9.72-1.el8_5.2.x86_64
(mariadb >= 3:10.3.27 if mariadb) is needed by mariadb-connector-c-3.1.11-2.el8_3.x86_64
(mariadb-connector-c-config = 3.1.11-2.el8_3 if mariadb-connector-c-config) is needed by mariadb-connector-c-3.1.11-2.el8_3.x86_64
rpmlib(RichDependencies) <= 4.12.0-1 is needed by mariadb-connector-c-3.1.11-2.el8_3.x86_64
(NetworkManager >= 1.20 or dhclient) is needed by dracut-network-049-191.git20210920.el8.x86_64
rpmlib(RichDependencies) <= 4.12.0-1 is needed by dracut-network-049-191.git20210920.el8.x86_64
(annobin if gcc) is needed by redhat-rpm-config-125-1.el8.noarch
rpmlib(RichDependencies) <= 4.12.0-1 is needed by redhat-rpm-config-125-1.el8.noarch
To diagnose the problem, try running: 'rpm -Va --nofiles --nodigest'.
You probably have corrupted RPMDB, running 'rpm --rebuilddb' might fix the issue.
The downloaded packages were saved in cache until the next successful transaction.
You can remove cached packages by executing 'dnf clean packages'.

# dnf remove redhat-rpm-config-9.1.0-88.el7.centos.noarch
# dnf remove perl-devel-5.16.3-299.el7_9.x86_64
# dnf remove python36-rpmconf-1.1.7-1.el7.1.noarch
# dnf remove python-syspurpose-1.24.54-1.el7.centos.x86_64

This might not be needed...
# dnf upgrade gcc
# rpm -e --nodeps gdbm-1.10-8.el7.x86_64
# rpm -i /var/cache/dnf/baseos-XXXXX/packages/gdbm-libs-1.18-1.el8.x86_64.rpm
```
Install new CentOS 8 kernel.
```
# dnf install kernel-core
```
Install CentOS 8.
```
# dnf groupupdate "Core" "Minimal Install"
```
Reboot.
```
# systemctl reboot
```
