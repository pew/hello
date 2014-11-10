# yosemite rtc alarm wakeup issue
fix hourly wake-up

```
sudo /usr/libexec/PlistBuddy -c "Add :ProgramArguments: string --no-multicast" /System/Library/LaunchDaemons/com.apple.discoveryd.plist
```

revert to default

```
sudo /usr/libexec/PlistBuddy -c Revert /System/Library/LaunchDaemons/com.apple.discoveryd.plist
```

[source](http://ispire.me/fix-yosemite-rtc-alarm-wakeup-issue/)