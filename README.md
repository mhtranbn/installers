# installers


This is install pixicore-PXE booting.
- Install go from moovweb/gvm:
```
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)

source /root/.gvm/scripts/gvm

apt-get install bison

gvm install go1.4

gvm use go1.4

export GOROOT_BOOTSTRAP=$GOROOT

gvm install go1.5

```
-Install pixicore:
```
git clone https://github.com/danderson/pixiecore

cd pixiecore

go build .

wget http://alpha.release.core-os.net/amd64-usr/current/coreos_production_pxe.vmlinuz

wget http://alpha.release.core-os.net/amd64-usr/current/coreos_production_pxe_image.cpio.gz

mv pixiecore /usr/bin

pixiecore -kernel coreos_production_pxe.vmlinuz -initrd coreos_production_pxe_image.cpio.gz --cmdline coreos.autologin
```
And now try to boot from another pc boot to Network to see pixicore run.
```
mkdir /tftpboot
```
-Download erpxe-1.2.tar.gz from http://sourceforge.net/projects/erpxe/files/ 
```
tar -zvxf erpxe-1.2.tar.gz
nano /etc/default/tftpd-hpa
apt-get install tftpd-hpa
apt-get update
--update-rc.d tftpd-hpa defaults
--apt-get install apache2
--update-rc.d apache2 defaults
--cp /tftpboot/bin/setup/erpxe-httpd.conf /etc/apache2/conf.d/
--mkdir /etc/apache2/conf.d
--cp /tftpboot/bin/setup/erpxe-httpd.conf /etc/apache2/conf.d/
--apt-get install nfs-kernel-server rpcbind
--cat /tftpboot/bin/setup/erpxe-exports > /etc/exports
--update-rc.d rpcbind enable
--apt-get install samba samba-common-bin
--useradd --no-create-home -s /dev/null erpxe
--cat /tftpboot/bin/setup/erpxe-smb.conf > /etc/samba/smb.conf
--smbpasswd -a erpxe
--smbpasswd -a root
```

