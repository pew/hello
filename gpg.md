# gpg (GNU Privacy Guard) pgp

## gpg
### encryption
    gpg -e -a --local-user myID -r friendID

### decryption
    gpg -d

## gpg-zip
### encrypt
    gpg-zip -e -o secure.gpg -r Jonas folder

### decrypt
    gpg-zip -d secure.gpg

## entropy!
    # install
    apt-get install rng-tools
    # run
    rngd -r /dev/urandom
    # kill
    pkill rngd
    # remove from autostart
    update-rc.d -f rng-tools remove
    
## export (secret) key
	gpg --output public.txt --armor --export XXXXXXXX 	gpg --output private.txt --armor --export-secret-key XXXXXXXX

## import (secret) key
	gpg --import public.txt
	gpg --allow-secret-key-import --import private.txt