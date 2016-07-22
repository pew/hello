# backup tools
* https://attic-backup.org/ - http://www.stavros.io/posts/holy-grail-backups/
* bup

# rsync full backup

```
 rsync -aAXviP --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / /dest
```
