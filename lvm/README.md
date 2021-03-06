## lvm
## 1. get info
#### PV (Physical Volume)
```bash
pvs
```
![pvs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/01_pvc.jpg?raw=true)
```bash
pvdisplay
```
![pvdisplay](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/02_pvdisplay.jpg?raw=true)
#### VG (Volume Group)
```bash
vgs
```
![vgs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/03_vgs.jpg?raw=true)
```bash
vgdisplay
```
![vgdisplay](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/04_vgdisplay.jpg?raw=true)
#### LV (Logical Volume)
```bash
lvs
```
![lvs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/05_lvs.jpg?raw=true)
```bash
lvdisplay
```
![lvdisplay](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/06_lvdisplay.jpg?raw=true)


## 2. add new disk 50Gb and get info about
```bash
fdisk -l
```
![fdisk01](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/07_fdisk01.jpg?raw=true)
### or
```bash
lvmdiskscan
```
![lvmdiskscan](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/08_lvmdiskscan.jpg?raw=true)


## 3. create `PV /dev/sdb`
```bash
pvcreate /dev/sdb
```
![pvcreate](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/09_pvcreate.jpg?raw=true)
```bash
lvmdiskscan -l
```
![pvcreate](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/10_lvmdiskscan.jpg?raw=true)



## 4. add `PV /dev/sdb` to `LV centos`
```bash
vgextend centos /dev/sdb
```
![vgextend](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/11_vgextend.jpg?raw=true)
### extend  
```bash
lvm lvextend -l +100%FREE /dev/centos/opt
```
![lvextend](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/12_lvextend.jpg?raw=true)
```bash
resize2fs -p /dev/mapper/centos-opt
```
![resize2fs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/13_resize2fs.jpg?raw=true)
### `resize2fs` support ext2/3/4, that's why we need `xfs_growfs` that support xfs
```bash
xfs_growfs /dev/mapper/centos-opt
```
![xfs_growfs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/14_xfs_growfs.jpg?raw=true)

```bash
vgreduce --removemissing --verbose --force centos
dmsetup info -c | grep opt
lsof | grep "253,2"
dmsetup ls --tree
lsblk
```
```bash
testdisk /dev/sdb
```
##################################################################################
### clean Disk
```bash
# wipefs /dev/sdb
offset               type
----------------------------------------------------------------
0x0                  xfs   [filesystem]
                     UUID:  72f2a607-8af7-44c0-83c2-f1565cd68a1a                     
```
Then run it with `-a` to erase those signatures:
```bash
# wipefs -a /dev/sdb
/dev/sdb: 4 bytes were erased at offset 0x00000000 (xfs): 58 46 53 42

# wipefs /dev/sdb
#
```

```bash
pvcreate --uuid "07b6hd-RunD-esW7-DvZn-0MDF-yi63-YcWuwA" --restorefile /etc/lvm/archive/centos_00002-207124849.vg /dev/sdc
vgcfgrestore  centos
lvchange -ay /dev/centos/opt
vgchange -ay centos

lvs -a -o +devices
```
reverse
```bash
pvcreate --uuid "07b6hd-RunD-esW7-DvZn-0MDF-yi63-YcWuwA" --restorefile /etc/lvm/archive/centos_00003-1938821530.vg /dev/sdb
vgcfgrestore  centos
lvs -a -o +devices
lvchange -ay /dev/centos/opt
fsck ?
```
