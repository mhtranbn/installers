# installers
# installers


This is install pixicore-PXE booting.
- Install go from moovweb/gvm:
```
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
export GOROOT_BOOTSTRAP=$GOROOT
export GOROOT_BOOTSTRAP=$GOROOT
``` 
--
```bash
--source /root/.gvm/scripts/gvm
``` 
```bash
``` --apt-get install bison
```bash
``` --gvm install go1.4
```bash
``` --gvm use go1.4
```bash
``` --export GOROOT_BOOTSTRAP=$GOROOT
```bash
``` --gvm install go1.5

-Install pixicore:
```bash
``` --git clone https://github.com/danderson/pixiecore
```bash
``` --cd pixiecore
```bash
``` --go build .
```bash
``` --wget http://alpha.release.core-os.net/amd64-usr/current/coreos_production_pxe.vmlinuz
```bash
``` --wget http://alpha.release.core-os.net/amd64-usr/current/coreos_production_pxe_image.cpio.gz
```bash
``` --mv pixiecore /usr/bin
```bash
``` --pixiecore -kernel coreos_production_pxe.vmlinuz -initrd coreos_production_pxe_image.cpio.gz --cmdline coreos.autologin

And now try to boot from another pc boot to Network to see pixicore run.

```
``` --mkdir /tftpboot
-Download erpxe-1.2.tar.gz from http://sourceforge.net/projects/erpxe/files/ 
```bash
``` --tar -zvxf erpxe-1.2.tar.gz
```bash
``` --nano /etc/default/tftpd-hpa
```bash
``` --apt-get install tftpd-hpa
```bash
``` --apt-get update
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

