# encfs linux

### install
    apt-get install encfs
    
### adding users to fuse group
    adduser jonas fuse

### setup encfs
    mkdir /opt/encrypted
    encfs /opt/encrypted /home/decrypted
    
### (u)mount
    encfs /opt/encrypted /home/decrypted --public
    fusermount -u /home/decrypted
    
### (u)mount encfs remote via ssh
    read -s pass;echo $pass|ssh user@server "encfs /source /target --public"
    ssh user@server -t "fusermount -u /target"

