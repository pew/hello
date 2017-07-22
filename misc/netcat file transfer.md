# netcat
### send / receive files
sender:
    
    tar -czf - folder|nc -l 9999
    
receiver:
    
    nc <senderip> 9999|tar xvf -
