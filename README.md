## Usage

Run new iTop 2.7.2-1 (see tags for other iTop versions) container named *lva-itop*:
```
sudo docker run -d -p 8000:80 --name=lva-itop --restart=always -v /$$/itop-backups:/var/www/html/data/backups editionslva/itop
```
Then go to [http://localhost:8000/](http://localhost:8000/) to continue the installation.

Install Postfix as Internet Site (Option 2) to send notifications : 

```
apt-get install postfix
mkfifo /var/spool/postfix/public/pickup
service postfix restart
```
### Useful scripts and helpers

The image ships with several useful scripts you can run like this:
```
sudo docker exec lva-itop /script-name.sh [script_params]
```


A cron setup helper is aboard:
```
sudo docker exec lva-itop /setup-itop-cron.sh Cron Pa$5w0rD
```
Then you should create iTop user account with login *Cron* and password *Pa$5w0rD* and grant him Administrator profile. The third argument (optional) is the absolute path to the log file or `--without-logs` key. By default, the log file is `/var/log/itop-cron.log`.



