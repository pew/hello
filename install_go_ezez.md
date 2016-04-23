# quick golang installation

because reasons.

linux:

```
wget -O- https://storage.googleapis.com/golang/go1.6.2.linux-amd64.tar.gz|tar -C /usr/local -xzf -
export PATH=$PATH:/usr/local/go/bin
mkdir $HOME/work
export GOPATH=$HOME/work
```
