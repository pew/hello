# common *find* commands

### find empty folders
    find /path -type d -empty
    find /path -type d -empty -exec rm -r {} \;
    
### find symbolic links
    find . -type l -exec ls -l {} \;
    
### find old files
    find /opt/*.tar.gz -mtime +4 -exec rm {} \;

### change permissions
    find /var/www/ -type -f -exec chmod 644 {} \;
    find /var/www/ -type -d -exec chmod 755 {} \;

### remove with xargs (folder names with white space)
    find ~/ -name '.DS_Store' -print0|xargs -0 rm

and with multiple matches (.md5, .txt and so on)

    find ~/Downloads/ -type f \( -name '*.sha256' -o -name '*.md5' -o -name '*.txt' \) -print0|xargs -0 rm
