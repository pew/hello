# git add && commit && push to every remote

    git add -A&&git commit -a -m "$(curl -s http://whatthecommit.com|perl -p0e '($_)=m{<p>(.+?)</p>}s')"&&for i in $(git remote);do git push $i master;done
