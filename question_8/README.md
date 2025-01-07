## Lemonade payments 
## Devops Engineer - Technical Assessment - submission
### Submitted by: Zack Mwangi [ zackmwangi@gmail.com ]
### Date: Jan 07, 2025

---

### Section 2: Coding Challenge
#### Q8: Write a script to restart the Laravel backend service if CPU usage exceeds 80%.
> ##### Ans:
> Script file(bash) in this same folder [>> click here to view file <<](./restart_laravel.sh)
> Uses a while loop to continuously monitor CPU usage and restart the Laravel service if the usage exceeds 80%.
> Checks every minute.

> Remember to make the script executable (chmod +x ./restart_laravel.sh)

```sh

#!/bin/bash

#Ensure systemd entry for this service is installed
SERVICE_NAME="lemonice-laravel.service"

#Declare value to observe
THRESHOLD_MAX_CPU_USAGE=80

# Loop indefinitely
while true; do

    # Calculate current CPU usage, read via top, grep value  and use regex matching to assign to variable
    CPU_USAGE=$(top -bn1 | grep "Cpu(s)" | sed "s/.*, *\([0-9.]*\)%* id.*/\1/" | awk '{print 100 - $1}')

    # Use boolean logic to check if threshold is exceeded
    # NOTE: -gt means "is greater than"
    
    if [ "$CPU_USAGE" -gt "$THRESHOLD_MAX_CPU_USAGE" ]; then

        # Output log message
        echo "CPU usage has exceeded $THRESHOLD_MAX_CPU_USAGE%. Restarting service $SERVICE_NAME."
        
        # restart service 
        sudo systemctl restart $SERVICE_NAME
        
        echo "$SERVICE_NAME was restarted."
    fi

    # check every 60 seconds
    sleep 60 

done

```



