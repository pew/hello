i forget this every.single.time.

```
youtube-dl -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/mp4' -o '%(playlist_index)s - %(title)s.%(ext)s' https://youtube.com/foo
```

download only 720p version:

```
youtube-dl -f 'bestvideo[ext=mp4,height<=720]+bestaudio[ext=m4a]/mp4' -o '%(playlist_index)s - %(title)s.%(ext)s' 'https://youtube.com/foo'
```