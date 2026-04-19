# systemctl basics

## Check service
systemctl status nginx
systemctl list-units --type=service --state=running
systemctl list-unit-files --type=service | grep enabled
systemctl cat bluetooth
## Start service
systemctl start nginx

## Restart
systemctl restart nginx