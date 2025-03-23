# Découverte de Nextcloud

## Post install

Se connecter à la VM hébergeant docker et executer les commandes bash suivantes:

```bash
sudo docker exec --user www-data -it nextcloud-app php occ config:system:set maintenance_window_start --type=integer --value=1
sudo docker exec --user www-data -it nextcloud-app php occ config:system:set default_phone_region --value="FR"
sudo docker exec --user www-data -it nextcloud-app php occ log:manage --level WARN
sudo docker exec --user www-data -it nextcloud-app php occ maintenance:repair --include-expensive
sudo docker exec --user www-data -it nextcloud-app php occ db:add-missing-indices
```

Après avoir activer, via le WebUI, le planification des tâches Cron, executer les commandes bash suivantes :

```bash
sudo -i
crontab -e
```

Insérer la ligne suivante :

```txt
*/5 * * * * /usr/bin/docker exec -u www-data nextcloud-app /usr/local/bin/php -f /var/www/html/cron.php --define apc.enable_cli=1
```
