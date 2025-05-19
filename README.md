# Вокруг PHP – экосистема веб-приложений

### Домашнее задание № 1.
Конфиг супервизора, положить в /etc/supervisor/conf.d

```
[program:worker]
process_name=%(program_name)s_%(process_num)02d
command=php8.2 ПУТЬДОФАЙЛА_RUNNER -c handle_events_daemon
autostart=true
autorestart=true
user=www-data
numprocs=1
redirect_stderr=true
stdout_logfile=/var/log/worker
```

```
php runner -c save_event --name 'name' --receiver 1 --text 'text' --cron '* * * * *' * * * * * php runner -c handle_events
```

### Решение:

Перемещаю файлы в нужную папку (в данном случае: /home/reminder-bot/php/learning/cur/), затем редактирую файл в супервизорде:

![Скриншот1](Image/Безымянный.png)

Получаю следующий конфиг:

![Скриншот2](Image/Безымянный2.png)

Перезагружаем супервизорд:

![Скриншот3](Image/Безымянный3.png)

Однако в моем случае после проверки статуса запуска возникает ошибка:

![Скриншот4](Image/Безымянный4.png), которая в данном случае решается добавлением строчки: ![Скриншот5](Image/Безымянный5.png) в конфиг

Итоговый конфиг:

![Скриншот6](Image/Безымянный6.png)

Снова перезагружаем супервизорд:

![Скриншот3](Image/Безымянный3.png)

Скрипт загрузился:

![Скриншот7](Image/Безымянный7.png)

Теперь попробую остановить процесс:

![Скриншот11](Image/Безымянный11.png)

Процесс перезапустился.
