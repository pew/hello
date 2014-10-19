# EBS Volumes:

pre-warming EBS Volumes (from snapshot):

    dd if=/dev/xvdf of=/dev/null bs=1M

pre-warming EBS Volumes (new, empty volume):

    dd if=/dev/zero of=/dev/xvdf bs=1M
