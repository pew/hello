```
dscl . -create /Users/username
dscl . -create /Users/username UserShell /bin/bash
dscl . -create /Users/username UniqueID 501
dscl . -create /Users/username PrimaryGroupID 20
dscl . -create /Users/username NFSHomeDirectory /Users/username
dscl . -create /Users/username RealName username
passwd username
```