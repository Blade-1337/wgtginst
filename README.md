# wgtg_inst

**Управляй своим Wireguard сервером через Telegram**

Проект находится на ранней стадии разработки (сырой).

---

## О проекте

Данный проект направлен на упрощение развертывания и управления виртуальной приватной сетью (VPN) спрособом интеграции сервера Wireguard и Telegram-бота.

### Функции:
- Развертывание Wireguard сетей.
- Упрощенное управление через Telegram.
- Генерация QR-кодов для подключения.

---

## Установка

### Скопируйте проект в каталог `/etc/`:
```
git clone 
```

### Настройте `config.py`:
1. Вставьте API Telegram-бота и ID пользователей, которым будет разрешен доступ к боту.
2. Пример:
```python
mainid = [123456789, 987654321]
api_tg = "YOUR_BOT_API"
```
3. Для получения ID Telegram пользователя воспользуйтесь ботом [@get_myidbot](https://t.me/get_myidbot).

---

## Запуск

### Через Python:
1. Установите зависимости:
   ```bash
   pip install --no-cache-dir -r requirements.txt
   ```
2. Запустите скрипт:
   ```bash
   python3 main.py
   ```

### Через Docker:
1. Запустите Docker Compose:
   ```bash
   docker compose up -d
   ```

---

## Создание сервиса скрипта (системный демон)
1. Создайте файл сервиса:
   ```bash
   sudo nano /etc/systemd/system/wgtginst.service
   ```
2. Добавьте следующий код:
   ```ini
   [Unit]
   Description=Wireguard Telegram Bot
   After=multi-user.target

   [Service]
   Type=idle
   ExecStart=/usr/bin/python /etc/wgtginst/main.py
   Restart=always

   [Install]
   WantedBy=multi-user.target
   ```
3. Активируйте сервис и запустите бота:
   ```bash
   sudo systemctl daemon-reload
   sudo systemctl enable wgtginst.service
   sudo systemctl start wgtginst.service
   ```

---

## Обратная связь
Если вы столкнулись с ошибками или хотите поделиться предложениями по улучшению, обращайтесь через [Issues](https://github.com/your-repo/issues).

---

## Лицензия
Данный проект продолжает активно развиваться. Свободно используйте или проводите модификации с учетом прав лицензии.

