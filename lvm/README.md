# lvm
## 1. get info
### PV (Physical Volume)
```bash
pvs
```
![pvs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/01_pvc.jpg?raw=true)
```bash
pvdisplay
```
![pvdisplay](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/02_pvdisplay.jpg?raw=true)
### VG (Volume Group)
```bash
vgs
```
![vgs](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/03_vgs.jpg?raw=true)
```bash
vgdisplay
```
![vgdisplay](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/04_vgdisplay.jpg?raw=true)
### LV (Logical Volume)
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
## 3. create PV
```bash
pvcreate /dev/sdb
```
![pvcreate](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/09_pvcreate.jpg.jpg?raw=true)


```bash
xfs_growfs /dev/centos/root
```
