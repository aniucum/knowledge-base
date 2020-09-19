# nfs
10.10.10.10 - server
10.10.10.11 - client

rpcinfo -p | grep nfs

yum install nfs-utils -y
systemctl start nfs && systemctl enable nfs


/etc/exports
/home/backup/ 10.10.10.0/24(rw,sync,no_root_squash)


showmount -e 10.10.10.10
mount -t nfs 10.10.10.10:/home/backup/ /var/opt/gitlab/backups/

umount /var/opt/gitlab/backups/
