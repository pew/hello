# cleanup ruby gem documentation
```
rm -r "$(gem env gemdir)"/doc/*
gem cleanup --dryrun
gem cleanup
```
