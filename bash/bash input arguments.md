# bash input arguments

## skip first argument, process 2nd and so on

```
#!/bin/bash

# get first argument
case $1 in
start)
        # get only 2nd and further arguments, skip first
        echo aws start-instances --instance-ids "${*:2}"

        echo aws start-instances --instance-ids ${*:2}
        ;;
*)
        echo yolo
        ;;
esac
```
