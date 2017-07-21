### UFW - Uncomplicated Firewall
    apt-get install ufw

### configure
    ufw allow 22/tcp
    ufw allow 80/tcp
    ufw allow 443/tcp

    ufw enable
    ufw status verbose

automatically for v4 and v6 (if available)

### configure tunnelbroker
    ufw allow from 216.66.22.2 proto ipv6

change ip.

### more info
    ufw status verbose