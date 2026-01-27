# Чеклист: Ручная проверка после развёртывания

## Сети

- Проверка открытых портов: `sudo ufw status` на обоих VM.

## Nginx

- Проверка редиректа HTTP → HTTPS: `curl -I http://<nginx_ip>`.
- Проверка HTTPS: `curl -k -I https://<nginx_ip>`.
- Логи: 
  - `sudo tail -n 20 /var/log/task1/nginx/app.devops.local.access.log`.
  - `sudo tail -n 20 /var/log/task1/nginx/app.devops.local.error.log`.

## Проверка бэкенда (на VM1)

- Проверка локального ответа: `curl -I http://localhost:5000`.
- Логи приложения: `tail -n 50 /var/log/task1/app.log`.

## Проверка PostgreSQL.

- Статус службы: `sudo systemctl status postgresql`.
- Проверка логов БД:  `sudo cat /var/log/postgresql/postgresql-14-main.log`.
- Проверка pg_hba.conf: `sudo cat /etc/postgresql/*/main/pg_hba.conf`.

## Проверка логов и cron** 

- Nginx:
  - `sudo cat /var/log/task1/nginx/app.devops.local.access.log`.
  - `sudo cat /var/log/task1/nginx/app.devops.local.error.log`.
- Приложение: `sudo cat /var/log/task1/app.log`.
- Backup: `sudo cat /var/log/task1/scripts/backup.log`.
- scripts: `sudo cat /var/log/task1/scripts/*.log`.
- БД:  `sudo cat /var/log/postgresql/postgresql-14-main.log`.
- Проверка cron-задач: `sudo crontab -u devops -l`.