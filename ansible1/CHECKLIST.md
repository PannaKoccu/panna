`Чеклист: Ручная проверка после развёртывания`
-
**Сети**
- Проверка открытых портов: `sudo ufw status` на обоих VM.
**Nginx**
- Проверка редиректа HTTP → HTTPS: `curl -I http://<nginx_ip>`.
- Проверка HTTPS: `curl -k -I https://<nginx_ip>`.
- Логи: 
  - `sudo tail -n 20 /var/log/nginx/app.devops.local.access.log`.
  - `sudo tail -n 20 /var/log/nginx/app.devops.local.error.log`.
**Проверка бэкенда (на VM1)**
- Проверка локального ответа: `curl -I http://localhost:5000`.
- Логи приложения: `tail -n 50 /var/log/task1/app.log`.
**Проверка PostgreSQL.**
- Статус службы: `sudo systemctl status postgresql`.
- Подключение от приложения: `psql -h localhost -U task1_user -d task1 -c "SELECT 1;"`.
- Проверка pg_hba.conf: `sudo cat /etc/postgresql/*/main/pg_hba.conf`.
**Проверка логов и cron** 
- Nginx:
  - `/var/log/nginx/app.devops.local.access.log`.
  - `/var/log/nginx/app.devops.local.error.log`.
- Приложение: `/var/log/task1/app.log`.
- Backup: `/var/log/task1/backup.log`.
- scripts: `/var/log/task1/*.log`.
- Проверка cron-задач: `sudo crontab -u devops -l`.