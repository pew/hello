# use proxy setting for chrome / chromium

use default system settings and use specific proxy settings for chrome or chromium

```
open -a /Applications/Google Chrome.app --args --proxy-server="socks5://host:port"
open -a ~/Applications/Chromium.app --args --proxy-server="socks5://localhost:1337"
```

create an applescript to open chrome with the correct settings with spotlight/launchbar/alfred and so on:

```
do shell script "open -a Chromium.app --args --proxy-server='socks5://localhost:1337'"
```

or, try: https://chrome.google.com/webstore/detail/proxy-switchy/caehdcpeofiiigpdhbabniblemipncjj
