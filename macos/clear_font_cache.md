# clear mac os x font cache
## run as root / sudo
```
atsutil databases -remove
atsutil server -shutdown
atsutil server -ping
```