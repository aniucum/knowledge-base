# lvm
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
### info about new disk
```bash
fdisk -l
```
![fdisk01](https://github.com/aniucum/knowledge-base/blob/master/lvm/images/07_fdisk01.jpg?raw=true)

```bash
xfs_growfs /dev/centos/root
```