# handbrake cli batch
```
for i in $(find . -name '*.avi');do echo HandBrakeCLI -Z iPad -i $i -o $i.mp4;done
```