[Spamhaus](https://www.spamhaus.org/) DROP/EDROP Lists for `iptables`
---
A shell script that grabs the latest [Spamhaus DROP and EDROP Lists](https://www.spamhaus.org/drop/), then adds them to `iptables`.

### Installation
```
# Download the script.
curl -LO https://github.com/phracker/spamhaus/raw/master/spamhaus.sh
# Make it executable.
chmod +x spamhaus.sh
# Execute it.
sudo ./spamhaus.sh
# Confirm the rules have been added.
sudo iptables -L Spamhaus -n
```

### Automatic Updating
In order for the list to automatically update each day, you'll need to set up a cron job using `crontab -e`.

This example rule will execute the script once daily at 3am.
```
0 3 * * * /path/to/spamhaus.sh
```

### Troubleshooting
If you need to remove all the Spamhaus rules, run the following:
```
sudo iptables -F Spamhaus
sudo iptables -F SpamhausAct
```
