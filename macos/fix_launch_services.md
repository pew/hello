# fix os x launch services

    /System/Library/Frameworks/CoreServices.framework/Versions/Current/Frameworks/LaunchServices.framework/Support/lsregister -kill -r -domain local -domain system -domain user
