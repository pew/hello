# wannabe linux sync (inotify)
install _inotify_ tools

    apt-get install inotify-tools

have a look at the manpages of inotifywait, see an example below. inotifywait watches a folder (including subfolders with -r option) for create and modify events and runs the sync.sh command if an event occured.

    while :;do inotifywait -r -e create -e modify $HOME/data/ && $HOME/sync.sh;done >/dev/null 2>&1
