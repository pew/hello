# periodic scripts LaunchDaemon
since my macbook is typically shut down (or bootet from another disk) I want to run the periodic maintenance scripts automatically every time I boot my mac.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>Label</key>
	<string>com.nobody.maintenance</string>
	<key>ProgramArguments</key>
	<array>
		<string>/usr/sbin/periodic</string>
		<string>daily</string>
		<string>weekly</string>
		<string>monthly</string>
	</array>
	<key>RunAtLoad</key>
	<true/>
</dict>
</plist>
```

save the contents above to

```
/Library/LaunchDaemons/com.nobody.maintenance.plist
```

and restart your mac. check the time stamps of the log files to see if the script run.

```
ls -ltr /var/log/*.out
```
