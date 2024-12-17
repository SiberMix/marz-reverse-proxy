# REVERSE_PROXY ([English](/README.md))
<p align="center"><a href="#"><img src="./media/marz.png" alt="Image" width="400" height="300"></a></p>

-----

### Прокси с использованием  VLESS-TCP-XTLS-Vision и VLESS-TCP-REALITY (Steal from yourself) за реверс-прокси NGINX
Этот скрипт предназначен для быстрой и простой настройки скрытого прокси-сервера, с маскировкой через NGINX. В данном варианте все входящие запросы обрабатываются NGINX, а сервер работает как прокси-сервер только при условии, что запрос содержит правильный путь (URI). Это повышает безопасность и помогает скрыть истинное назначение сервера.

> [!IMPORTANT]
> Этот скрипт был протестирован на Debian 12 в среде виртуализации KVM. Для корректной работы вам потребуется собственный домен, который необходимо привязать к Cloudflare. Скрипт рекомендуется запускать с правами root на свежеустановленной системе.

> [!NOTE]
> Скрипт настроен с учётом специфики маршрутизации для пользователей из России.

-----

### Настройка cloudflare
1. Обновите систему и перезагрузите сервер.
2. Настройте Cloudflare:
   - Привяжите ваш домен к Cloudflare.
   - Добавьте следующие DNS записи:

| Type  | Name             | Content          | Proxy status  |
| ----- | ---------------- | ---------------- | ------------- |
| A     | your_domain_name | your_server_ip   | DNS only      |
| CNAME | www              | your_domain_name | DNS only      |
   
3. Настройки SSL/TLS в Cloudflare:
   - Перейдите в раздел SSL/TLS > Overview и выберите Full для параметра Configure.
   - Установите Minimum TLS Version на TLS 1.3.
   - Включите TLS 1.3 (true) в разделе Edge Certificates.

-----

### Включает в себя:
  
1. Конфигурация сервера Xray с MARZBAN:
   - VLESS-TCP-XTLS-Vision и VLESS-TCP-REALITY (Steal from yourself).
   - Подключение подписки для автоматического обновления конфигураций.
   - [Пользовательская подписка](https://github.com/x0sina/marzban-sub).
   - [Блокировщик торрентов](https://github.com/kutovoys/marzban-torrent-blocker).
   - [Ограничение IP-адресов](https://github.com/houshmand-2005/V2IpLimit).
2. Настройку обратного прокси NGINX на порт 443.
3. Обеспечение безопасности:
   - Автоматические обновления системы через unattended-upgrades.
4. Настройка SSL сертификатов Cloudflare с автоматическим обновлением для защиты соединений.
5. Настройка WARP для защиты трафика.
6. Включение BBR — улучшение производительности TCP-соединений.
7. Настройка UFW (Uncomplicated Firewall) для управления доступом.
8. Настройка SSH, для обеспечения минимально необходимой безопасности.
9. Отключение IPv6 для предотвращения возможных уязвимостей.
10. Шифрование DNS-запросов с использованием systemd-resolved (DoT) или AdGuard Home (DoH-DoT).
11. Выбор случайного веб-сайта из массива для добавления дополнительного уровня конфиденциальности и сложности для анализа трафика.
-----

### Установка REVERSE_PROXY:

Для начала настройки сервера выполните следующую команду в терминале:
```sh
bash <(curl -Ls https://github.com/cortez24rus/marz-reverse-proxy/raw/refs/heads/main/reverse_proxy_server.sh)
```


### Выбор и установка случайного шаблона для веб-сайта:
```sh
bash <(curl -Ls https://github.com/cortez24rus/marz-reverse-proxy/raw/refs/heads/main/reverse_proxy_random_site.sh)
```

Скрипт запросит у вас необходимую конфигурационную информацию:

<p align="center"><a href="#"><img src="./media/marz_rp_install_RU.png" alt="Image"></a></p>

### Примечание: 
- После завершения настройки скрипт отобразит все необходимые ссылки и данные для входа в административную панель MARZBAN.
- Все конфигурации можно будет изменять по мере необходимости, благодаря гибкости настроек.

-----

### Если этот скрипт был полезен для вас, поставьте ему звезду ⭐

-----

## Количество звезд по времени
[![Stargazers over time](https://starchart.cc/cortez24rus/marz-reverse-proxy.svg?variant=adaptive)](https://starchart.cc/cortez24rus/marz-reverse-proxy)
