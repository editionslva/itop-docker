## Usage

Run new iTop 2.7.2-1 (see tags for other iTop versions) container named *lva-itop*:
```
docker volume create lva-itop-backups
docker run -d -p 8000:80 --mount type=volume,target=/var/www/html/data/backups,src=lva-itop-backups --restart=always --name=lva-itop editionslva/itop
```
Then go to [http://localhost:8000/](http://localhost:8000/) to continue the installation.

Install Postfix as Internet Site (Option 2) to send notifications : 

```
docker exec -ti lva-itop apt-get install postfix
docker exec -ti lva-itop mkfifo /var/spool/postfix/public/pickup
docker exec -ti lva-itop service postfix restart
docker exec -ti lva-itop chown -R www-data:www-data /var/www/html/data/backups
```
### Useful scripts and helpers


A cron setup helper is aboard:
```
docker exec -ti lva-itop /setup-itop-cron.sh Cron Pa$5w0rD
```
Then you should create iTop user account with login *Cron* and password *Pa$5w0rD* and grant him Administrator profile. The third argument (optional) is the absolute path to the log file or `--without-logs` key. By default, the log file is `/var/log/itop-cron.log`.



