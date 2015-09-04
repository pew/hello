# watch folders for changes with inotifywatch and send a mail with the changed/added/modified file

```
inotifywait -m -r -q --format '%f' -e modify /mnt/folder_to_watch|while read FILE;do echo "body of mail" | mutt -a "/mnt/folder_to_watch/$FILE" -s "subject" -- user@example.com;done
```
