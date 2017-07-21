# ecryptfs for individual folder

`/data.home` holds the encrypted data, `/data/home` the decrypted.

**prep**

```
root $ mkdir -p /data/.home /data/home ~/.ecryptfs
root $ echo "/data/.home /data/home ecryptfs" > ~/.ecryptfs/data.conf
root $ ecryptfs-add-passphrase
```

note the password and also the signature.

**mount and umount**

```
root $ echo "the signature from the above command" > ~/.ecryptfs/data.sig
root $ mount.ecryptfs_private data
root $ umount.ecryptfs_private data
```

**mount mount mount**

umount will also clear the session keyring, so next time you want to mount it:

```
root $ ecryptfs-add-passphrase
root $ mount.ecryptfs_private data
```

gj!