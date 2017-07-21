# bash parameter expansion
### search and replace
remove *.m4a* part

```
ffmpeg -i $i ${i/.m4a/}.mp3;done
```