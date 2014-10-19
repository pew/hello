# subreddit download
### install jshon
### list:
    curl -sS http://www.reddit.com/r/earthporn.json|jshon -e data -e children -a -e data -e url -u|grep '.\(jpe\|jp\|pn\)g$'
### wget:    
    curl -sS http://www.reddit.com/r/earthporn.json|jshon -e data -e children -a -e data -e url -u|grep '.\(jpe\|jp\|pn\)g$'|xargs wget

