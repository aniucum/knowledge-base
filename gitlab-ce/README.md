### gitlab backup
```bash
gitlab-rake gitlab:backup:create
```
### gitlab restore
```bash
sudo cp 11493107454_2018_04_25_10.6.4-ce_gitlab_backup.tar /var/opt/gitlab/backups/
sudo chown git.git /var/opt/gitlab/backups/11493107454_2018_04_25_10.6.4-ce_gitlab_backup.tar
```

```bash
sudo gitlab-ctl stop unicorn
sudo gitlab-ctl stop puma
sudo gitlab-ctl stop sidekiq
# Verify
sudo gitlab-ctl status
```

```bash
# This command will overwrite the contents of your GitLab database!
sudo gitlab-backup restore BACKUP=11493107454_2018_04_25_10.6.4-ce
```
```bash
sudo gitlab-ctl reconfigure
sudo gitlab-ctl restart
sudo gitlab-rake gitlab:check SANITIZE=true
```
