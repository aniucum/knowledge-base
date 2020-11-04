# rsync
```bash
#centos
yum install rsync
#debian
apt-get install rsync
```

```bash
#local
rsync --archive --verbose --progress /source/ /destination/
#from remote server
rsync --archive --verbose --progress user@remotehost:/remote/source/ /local/destination/
#to remote server
rsync --archive --verbose --progress /local/source/ user@remotehost:/remote/destination/
```
A `trailing slash` on the source changes this behavior to avoid creating an additional directory level at the destination. You can think of a trailing / on a source as meaning "copy the contents of this directory" as opposed to "copy the directory by name", but in both cases the attributes of the containing directory are transferred to the containing directory on the destination. In other words, each of the follow‐ ing commands copies the files in the same way, including their setting of the attributes of /dest/foo:
