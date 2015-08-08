# hdiutil
### attach sparsebundle read only
	hdiutil attach http://my.webserver.com/master.dmg -shadow /tmp/mastershadowfile

### create encrypted sparsebundle

```
hdiutil create -encryption AES-256 -fs HFS+J -size 50g -volname "VolumeName" filename.sparsebundle
```
