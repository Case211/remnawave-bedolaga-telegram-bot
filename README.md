# 🤖 Remnawave Bedolaga Bot

<div align="center">

[![Docker Image](https://img.shields.io/badge/Docker-fr1ngg/remnawave--bedolaga--telegram--bot-blue?logo=docker&logoColor=white)](https://hub.docker.com/r/fr1ngg/remnawave-bedolaga-telegram-bot)
[![Python](https://img.shields.io/badge/Python-3.11+-blue?logo=python&logoColor=white)](https://python.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-blue?logo=postgresql&logoColor=white)](https://postgresql.org)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Stars](https://img.shields.io/github/stars/Fr1ngg/remnawave-bedolaga-telegram-bot?style=social)](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/stargazers)

![Logo](./assets/logo2.svg)

**Современный Telegram-бот для управления VPN подписками через Remnawave API**

*Полнофункциональное решение с управлением пользователями, платежами и администрированием*

[🚀 Быстрый старт](#-быстрый-старт) • [📖 Документация](#-документация) • [💬 Поддержка](#-поддержка) • [🤝 Вклад](#-вклад-в-проект)

</div>

---

## ✨ Основные возможности

<table>
<tr>
<td width="50%">

### 👤 **Для пользователей**
- 💰 **Управление балансом** - Telegram Stars + Telegram Tribute + P2P через поддержку
- 🛒 **Покупка подписок** - различные тарифы с настройкой squad
- 📱 **Управление подписками** - просмотр, продление, ссылки, настройка автопродления
- 🎁 **Промокоды** - денежные бонусы
- 👥 **Реферальная программа** - зарабатывай с друзей и их последующих пополнений
- 🎰 **Игра удачи** - ежедневные бонусы
- 🆓 **Тестовая подписка** - бесплатная пробная версия
- ♾️ **Автопродление** - настраиваемое автообновление
- 🌐 **Мультиязычность** - русский и английский

</td>
<td width="50%">

### ⚙️ **Для администраторов**
- 📊 **Детальная статистика** - пользователи, платежи, подписки
- 👥 **Управление пользователями** - поиск, редактирование, баланс
- 💳 **Управление платежами** - одобрение, история, Telegram Stars
- 🎫 **Управление промокодами** - создание, статистика, массовые операции
- 🖥 **Мониторинг системы** - состояние нод, синхронизация с Remnawave
- 📨 **Рассылки** - уведомления пользователям
- 🔍 **Мониторинг подписок** - автоуведомления об истечении
- 📋 **Правила сервиса** - настройка через админ-панель
- ♾️ **Статистика автопродления** - полный контроль

</td>
</tr>
</table>

---

# 🚀 Автоматическая установка 

- Данный скрипт не был полноценно протестирован, тестировался на чистом сервере, возможно придется собирать докер файл и делать reverse proxy самостоятельно, делайте резервные копии, автор никакой ответственности не несет за ваши полетевшие Nginx/Caddy в случае настройки автоматической через скрипт!

## Быстрая установка одной командой

```bash
curl -fsSL https://raw.githubusercontent.com/Case211/remnawave-bedolaga-telegram-bot/main/bedolaga.sh | sudo bash
```

Или скачайте и запустите:

```bash
wget https://raw.githubusercontent.com/Case211/remnawave-bedolaga-telegram-bot/main/bedolaga.sh
chmod +x bedolaga.sh
sudo ./bedolaga.sh
```

## 📋 Типы установки

Скрипт поддерживает 5 различных конфигураций установки:

### 1. 🔧 Только бот (внешняя панель)
Подходит когда панель Remnawave находится на другом сервере.

**Особенности:**
- Отдельная PostgreSQL для бота
- Прямое подключение к внешней панели
- Независимая сетевая конфигурация

### 2. 🔗 Панель + бот на одном сервере
Рекомендуемый вариант для большинства случаев.

**Особенности:**
- Использует существующую сеть `remnawave-network`
- Внутреннее подключение между контейнерами
- Оптимальная производительность

### 3. 📦 Расширенная конфигурация
Включает дополнительные сервисы для высоконагруженных установок.

**Включает:**
- Redis для кэширования
- Nginx для статических файлов
- Расширенная сетевая конфигурация

### 4. 🌐 Бот с webhook через Caddy
Автоматическая настройка webhook с Caddy reverse proxy.

**Возможности:**
- Автоматический SSL (Let's Encrypt)
- Встроенный или внешний Caddy
- Health check endpoints
- Защита от DDoS

### 5. ⚡ Бот с webhook через Nginx
Webhook с Nginx для максимальной производительности.

**Возможности:**
- Продвинутая конфигурация Nginx
- Rate limiting
- SSL/TLS настройки
- Security headers

## 🔧 Процесс установки

### Шаг 1: Выбор типа установки
```
Выберите конфигурацию установки:
1) Только бот (панель RemnaWave на другом сервере)
2) Панель + бот на одном сервере (рекомендуется)
3) Расширенная - с Redis и Nginx
4) Бот с webhook через Caddy
5) Бот с webhook через Nginx

Ваш выбор (1-5): 4
```

### Шаг 2: Настройка домена (для webhook)
```
Введите домен для webhook (например: bot.example.com): your-bot.domain.com
У вас уже установлен Caddy? (y/n): n
```

### Шаг 3: Базовая конфигурация
```
Введите BOT_TOKEN: 1234567890:AAAA...
Введите BOT_USERNAME (без @): your_bot
Введите ADMIN_IDS (через запятую): 123456789,987654321
```

### Шаг 4: Настройки Remnawave
```
Введите REMNAWAVE_URL: https://your-panel.com
Введите REMNAWAVE_TOKEN: your_api_token
Введите SUBSCRIPTION_BASE_URL: https://sub.your-domain.com
```

### Шаг 5: Дополнительные настройки
- Настройка триал-периода
- Реферальная система
- Оплата Telegram Stars
- Мониторинг и автоудаление

## 🎛️ Управление ботом

После установки доступно интерактивное меню управления:

```bash
sudo ./bedolaga.sh
```

### Доступные действия:

#### 🚀 Управление
- **Запуск/остановка/перезапуск** бота
- **Обновление** до последней версии
- **Просмотр логов** в реальном времени

#### 💾 База данных
- **Создание резервных копий** БД
- **Восстановление** из резервной копии
- **Диагностика** состояния БД
- **Экстренное исправление** проблем

#### ⚙️ Конфигурация
- **Редактирование** .env файла
- **Просмотр конфигурации** webhook
- **Проверка статуса** всех сервисов

#### 🗑️ Очистка
- **Удаление базы данных**
- **Полное удаление** бота

## 🌐 Webhook конфигурация

### Автоматически создаваемые endpoints:

| Endpoint | Описание |
|----------|----------|
| `https://domain.com/webhook` | Основной webhook для Telegram |
| `https://domain.com/health` | Health check для мониторинга |

### Автоматическая генерация:
- **Webhook Secret** - случайный 64-символьный ключ
- **SSL сертификаты** через Let's Encrypt
- **Security headers** для защиты
- **Rate limiting** против злоупотреблений

## 📊 Мониторинг и логи

### Просмотр статуса:
```bash
# Статус всех контейнеров
docker compose ps

# Логи бота в реальном времени
docker compose logs -f bot

# Проверка webhook
curl https://your-domain.com/health
```

### Системная служба:
```bash
# Управление через systemctl
sudo systemctl start bedolaga-bot
sudo systemctl stop bedolaga-bot
sudo systemctl status bedolaga-bot
```

## 🔒 Безопасность

### Встроенная защита:
- **Rate limiting** - защита от спама
- **Security headers** - защита от XSS/CSRF
- **SSL/TLS** - шифрование трафика
- **Firewall ready** - готов к настройке UFW

### Рекомендуемые настройки UFW:
```bash
# Базовая защита
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Разрешить SSH
sudo ufw allow ssh

# Разрешить HTTP/HTTPS для webhook
sudo ufw allow 80
sudo ufw allow 443

# Включить firewall
sudo ufw enable
```

## 🔧 Устранение неполадок

### Распространенные проблемы:

#### Бот не запускается
```bash
# Проверить логи
docker compose logs bot

# Проверить конфигурацию
cat /opt/bedolaga-bot/.env
```

#### Webhook недоступен
```bash
# Проверить DNS
nslookup your-domain.com

# Проверить порты
netstat -tlnp | grep :443

# Проверить SSL
openssl s_client -connect your-domain.com:443
```

#### Проблемы с базой данных
```bash
# Запустить диагностику
sudo ./bedolaga.sh
# Выбрать пункт "Диагностика базы данных"

# Или экстренное исправление
# Выбрать пункт "Экстренное исправление БД"
```

## 📁 Структура файлов

```
/opt/bedolaga-bot/
├── docker-compose.yml    # Конфигурация Docker
├── .env                  # Переменные окружения
├── Caddyfile            # Конфигурация Caddy (если используется)
├── nginx.conf           # Конфигурация Nginx (если используется)
├── logs/                # Логи бота
├── data/                # Данные приложения
└── backup_*.sql         # Резервные копии БД
```

## 🔄 Обновление

Автоматическое обновление через меню:
```bash
sudo ./bedolaga.sh
# Выбрать "Обновить бота"
```

Или вручную:
```bash
cd /opt/bedolaga-bot
docker compose pull bot
docker compose up -d
```

## 💡 Полезные команды

# Быстрый перезапуск
docker compose restart bot

# Очистка логов
docker compose logs --tail=100 bot

# Проверка использования ресурсов
docker stats

# Резервная копия одной командой
docker compose exec postgres pg_dump -U remnawave_user remnawave_bot > backup.sql

<details>
<summary>🎁 Реферальная программа</summary>

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `REFERRAL_FIRST_REWARD` | Награда за первого реферала | `100.0` |
| `REFERRAL_REFERRED_BONUS` | Бонус приглашенному | `100.0` |
| `REFERRAL_THRESHOLD` | Порог активации (руб.) | `200.0` |
| `REFERRAL_PERCENTAGE` | % с последующих платежей | `0.2` (20%) |

</details>

<details>
<summary>⭐ Telegram Stars</summary>

| Переменная | Описание | Пример |
|------------|----------|---------|
| `STARS_ENABLED` | Включить оплату звездами | `true` |
| `STARS_100_RATE` | Курс 100 звезд → рублей | `110` |
| `STARS_250_RATE` | Курс 250 звезд → рублей | `280` |
| `STARS_500_RATE` | Курс 500 звезд → рублей | `550` |

</details>

<details>
<summary>⭐ Telegram Tribute</summary>

| Переменная | Описание | Пример |
|------------|----------|---------|
| `TRIBUTE_ENABLED` | Включить оплату с помощью доната на Tribute | `false` |
| `TRIBUTE_API_KEY` | API ключ из настроек Tribute | `XXXXXXXXXXX` |
| `TRIBUTE_WEBHOOK_PORT` | Порт | `8081` |
| `TRIBUTE_WEBHOOK_PATH` | URL Webhook Path | `/tribute-webhook` |
| `TRIBUTE_DONATE_LINK` | Ссылка на ваш донат из Tribute | `https://t.me/tribute/app?startapp=XXXXXXXXXXXXX` |

</details>

<details>
<summary>🔍 Мониторинг подписок</summary>

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `MONITOR_ENABLED` | Включить мониторинг | `true` |
| `MONITOR_CHECK_INTERVAL` | Интервал проверки (сек) | `1800` (30 мин) |
| `MONITOR_WARNING_DAYS` | За сколько дней предупреждать | `3` |
| `AUTO_DELETE_ENABLED` | Автоудаление истекших | `true` |

</details>

<details>
<summary> Триал</summary>

| Переменная | Описание | По умолчанию |
|------------|----------|--------------|
| `TRIAL_ENABLED` | Включить триал | `true` |
| `TRIAL_DURATION_DAYS` | Дней триала | `3` |
| `TRIAL_SQUAD_UUID` | Сквад триальной подписки | `` |
| `TRIAL_NOTIFICATION_ENABLED` | Уведомление об истечении триал подписки | `true` |
| `TRIAL_NOTIFICATION_HOURS_AFTER` | Через сколько отсылать сообщение  | `1` |
| `TRIAL_NOTIFICATION_HOURS_WINDOW` | Через сколько выслать повторно  | `` |

</details>
<details>
<summary>⚙️ Настройка Telegram Tribute</summary>

0) Обновляемся до версии 1.4.0
1) Регистрируемся и проходим верификацию в Tribute
2) Создаем донат ссылку, копируем вставляем в .env бота, конфигурируем остальные параметры из .env.example для работы Tribute
3) Настраиваем обратное прокси на /tribute-webhook

3.1 Пример для докера Caddy 

    https://test.example.com {
        # Tribute webhook endpoint
        handle /tribute-webhook* {
            reverse_proxy localhost:8081 {
                header_up Host {host}
                header_up X-Real-IP {remote_host}
            }
        }
    
        # Health check для webhook сервиса
        handle /webhook-health {
            reverse_proxy localhost:8081/health {
                header_up Host {host}
                header_up X-Real-IP {remote_host}
            }
        }

3.2 Пример для докера с Nginx 

     server {
        listen 80;
        server_name yourdomain.com;

        location /tribute-webhook {
            proxy_pass http://127.0.0.1:8081;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        
            proxy_connect_timeout 60s;
            proxy_send_timeout 60s;
            proxy_read_timeout 60s;
        
            client_max_body_size 10M;
        }

        location /webhook-health {
            proxy_pass http://127.0.0.1:8081/health;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
    }

3.3 Рестартим Бота, рестратим Caddy/Nginx   

4) Указываем ссылку на наш хук в настройках Tribute: https://test.example.com/tribute-webhook, создаем API ключ вписываем в .env бота

5) Делаем тест - если успешно, значит все настроили правильно. Не успешный тест - проверяй доступность хука, где-то ты что-то не так настроил
   
6) Тестируем пополнение через бота


</details>

🐳 Docker Compose примеры

<details>
<summary>🏠 Для локальной установки (панель + бот)</summary>

```yaml
services:
  postgres:
    image: postgres:15-alpine
    container_name: remnawave_bot_db
    restart: unless-stopped
    environment:
      POSTGRES_DB: remnawave_bot
      POSTGRES_USER: remnawave_user
      POSTGRES_PASSWORD: secure_password_123
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - remnawave-network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U remnawave_user -d remnawave_bot"]

  bot:
    image: fr1ngg/remnawave-bedolaga-telegram-bot:latest
    container_name: remnawave_bot
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    env_file:
      - .env
    environment:
      DATABASE_URL: postgresql+asyncpg://remnawave_user:secure_password_123@postgres:5432/remnawave_bot
    volumes:
      - ./logs:/app/logs
      - ./data:/app/data
    ports:
      - "8081:8081"
    networks:
      - remnawave-network

volumes:
  postgres_data:

networks:
  bot_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
```

</details>

<details>
<summary>🌐 Для удаленной установки</summary>

```yaml
services:
  postgres:
    image: postgres:15-alpine
    container_name: remnawave_bot_db
    restart: unless-stopped
    environment:
      POSTGRES_DB: remnawave_bot
      POSTGRES_USER: remnawave_user
      POSTGRES_PASSWORD: secure_password_123
    volumes:
      - postgres_data:/var/lib/postgresql/data
    networks:
      - bot_network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U remnawave_user -d remnawave_bot"]

  bot:
    image: fr1ngg/remnawave-bedolaga-telegram-bot:latest
    container_name: remnawave_bot
    restart: unless-stopped
    depends_on:
      postgres:
        condition: service_healthy
    env_file:
      - .env
    environment:
      DATABASE_URL: postgresql+asyncpg://remnawave_user:secure_password_123@postgres:5432/remnawave_bot
    volumes:
      - ./logs:/app/logs
      - ./data:/app/data
    ports:
      - "8081:8081"
    networks:
      - bot_network

volumes:
  postgres_data:

networks:
  bot_network:
    driver: bridge
    ipam:
      config:
        - subnet: 172.20.0.0/16
```

</details>

---

## 🎯 Использование

### 👤 Для пользователей

1. **Запуск** → Найдите бота и нажмите `/start`
2. **Язык** → Выберите русский или английский  
3. **Баланс** → "💰 Баланс" → "💳 Пополнить" → Telegram Stars
4. **Подписка** → "🛒 Купить подписку" → выбор тарифа → оплата
5. **Управление** → "📋 Мои подписки" → выбор → получение ссылки
6. **Рефералы** → "👥 Рефералы" → поделиться ссылкой

### ⚙️ Для администраторов

Доступ через кнопку **"⚙️ Админ панель"**:

- **📦 Управление подписками** → создание и настройка тарифов
- **👥 Управление пользователями** → поиск, редактирование балансов
- **💰 Управление платежами** → одобрение Telegram Stars платежей
- **🎁 Промокоды** → создание денежных бонусов
- **📨 Рассылки** → уведомления пользователям
- **🖥 Система Remnawave** → мониторинг нод, синхронизация
- **📊 Статистика** → подробная аналитика

---

## 📊 Производительность

### 💪 Рекомендуемые ресурсы

| Пользователей | RAM | CPU | Диск | Описание |
|---------------|-----|-----|------|----------|
| **До 500** | 1GB | 1 vCPU | 10GB | Начальная конфигурация |
| **До 1,000** | 2GB | 1 vCPU | 20GB | Малый бизнес |
| **До 10,000** | 4GB | 2 vCPU | 50GB | Средний бизнес |
| **До 50,000** | 8GB | 4 vCPU | 100GB | Крупный бизнес |

### ⚡ Оптимизация

- **Redis** → включите для кэширования (`--profile with-redis`)
- **PostgreSQL** → настройте для production нагрузок
- **Nginx** → используйте как reverse proxy (`--profile with-nginx`)
- **Мониторинг** → отслеживайте через `docker stats`

---

## 🔧 Управление

### 📋 Основные команды

```bash
# Переход в директорию
cd /opt/bedolaga-bot

# Управление через Docker Compose
docker compose up -d           # Запуск
docker compose down            # Остановка  
docker compose restart bot     # Перезапуск бота
docker compose logs -f bot     # Логи в реальном времени

# Управление через systemd (если настроено)
sudo systemctl start bedolaga-bot
sudo systemctl stop bedolaga-bot
sudo systemctl restart bedolaga-bot
```

### 🔄 Обновление

```bash
# Автоматическое через меню
sudo ./bedolaga.sh

# Ручное обновление
docker compose down
docker compose pull bot
docker compose up -d
```

### 💾 Резервное копирование

```bash
# Создание backup
docker exec remnawave_bot_db pg_dump -U remnawave_user remnawave_bot > backup.sql

# Восстановление
docker exec -i remnawave_bot_db psql -U remnawave_user remnawave_bot < backup.sql
```

---

## 🐛 Устранение неполадок

### ❓ Частые проблемы

<details>
<summary>🤖 Бот не отвечает</summary>

**Проверьте:**
- ✅ Правильность `BOT_TOKEN`
- ✅ Интернет соединение
- ✅ Логи: `docker compose logs bot`

**Решение:**
```bash
# Перезапуск бота
docker compose restart bot

# Проверка токена
docker exec remnawave_bot env | grep BOT_TOKEN
```

</details>

<details>
<summary>🗄️ Ошибки базы данных</summary>

**Симптомы:**
- SQL ошибки в логах
- Бот не сохраняет данные

**Решение:**
```bash
# Проверка PostgreSQL
docker compose logs postgres

# Подключение к БД
docker exec -it remnawave_bot_db psql -U remnawave_user remnawave_bot

# Экстренное восстановление через меню
sudo ./bedolaga.sh → "10) Экстренное исправление БД"
```

</details>

<details>
<summary>🔌 Проблемы с Remnawave API</summary>

**Проверьте:**
- ✅ Доступность `REMNAWAVE_URL`
- ✅ Валидность `REMNAWAVE_TOKEN`
- ✅ Сетевое подключение

**Диагностика:**
```bash
# Проверка URL
curl -I https://your-panel.com

# Тест API из контейнера
docker exec remnawave_bot curl -I http://remnawave:3000
```

</details>

<details>
<summary>⚠️ Проблема обновления 1.3.3 → 1.3.4</summary>

**Симптом:** SQL ошибки после обновления связанные с автоплатежами

**Решение через меню:**
```bash
sudo ./bedolaga.sh
# Выберите: "10) Экстренное исправление БД (Python)"
# Или: "11) Экстренное исправление БД (SQL)"
```

**Ручное решение:**
1. Скачайте `emergency_fix.py`
2. Добавьте в `docker-compose.yml`:
```yaml
emergency-fix:
  image: fr1ngg/remnawave-bedolaga-telegram-bot:latest
  volumes:
    - ./emergency_fix.py:/app/emergency_fix.py
  environment:
    - DATABASE_URL=postgresql+asyncpg://remnawave_user:secure_password_123@postgres:5432/remnawave_bot
  networks:
    - bot_network
  profiles:
    - emergency
  command: python emergency_fix.py
```
3. Запустите: `docker compose run --rm emergency-fix`

</details>

---

## 🗺️ Roadmap

### ✅ Реализовано

- ✅ **Мониторинг подписок** - автоуведомления и контроль
- ✅ **Telegram Stars** - пополнение баланса звездами  
- ✅ **Синхронизация Remnawave** - импорт пользователей и статистика
- ✅ **Реферальная система** - полнофункциональная программа
- ✅ **Игра удачи** - ежедневные розыгрыши бонусов
- ✅ **Управление промокодами** - создание, редактирование, статистика
- ✅ **Правила сервиса** - настройка через админ-панель
- ✅ **Автоплатежи** - настраиваемое автопродление подписок
- ✅ **Просмотр подписок пользователей** - детальная статистика
- - ✅ **Автоматическое пополнение лк с помощью доната Tribute**
### 🎯 В планах

| Версия | Функция | Приоритет | Описание |
|--------|---------|-----------|----------|
| **v1.4.5** | Юкасса интеграция | 🔴 High | Автоматические платежи |
| **v1.4.5** | Веб-панель управления | 🟡 Medium | Полный веб-интерфейс |
| **v1.4.5** | Безопасное удаление | 🟡 Medium | Архивирование вместо удаления |
| **v1.5.0** | Дополнительные платежи | 🟡 Medium | Сбербанк, Tinkoff, Crypto |
| **v1.5.0** | Уведомления | 🟡 Medium | Webhook, Email, другие чаты |
| **v1.6.0** | Система блокировок | 🟢 Low | Бан/разбан пользователей |

### 💡 Хотите добавить функцию?

- 🐛 [Сообщите о баге](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/issues)
- ✨ [Предложите улучшение](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/discussions)
- 🔧 [Создайте Pull Request](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/pulls)

---

## 🤝 Вклад в проект

### 💪 Как помочь

**🔧 Разработчикам:**
- Fork репозитория
- Создайте feature branch: `git checkout -b feature/amazing-feature`
- Внесите изменения и сделайте commit: `git commit -m 'Add amazing feature'`
- Push в branch: `git push origin feature/amazing-feature`
- Создайте Pull Request

**🐞 Пользователям:**
- Сообщайте о багах в [Issues](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/issues)
- Предлагайте идеи в [Discussions](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/discussions)
- Ставьте ⭐ проекту
- Рассказывайте друзьям

**💰 Спонсорам:**
- Поддержите разработку
- Закажите приоритетные функции
- Получите корпоративную поддержку

---

## 💬 Поддержка

### 📞 Контакты

- **Telegram:** [@fringg](https://t.me/fringg) - Писать исключительно по делу, я бы конечно был рад всем помочь настроить remnawave, ваши ноды, настроить вам бота, настроить вебхуки, но ребят я один и бота пилю тоже в соло, помощь вам занимает крайне много времени, поэтому если надумаете просить помочь что-то настроить, готовьтесь дарить мне шпагу подарком в тг)(
  
- **Issues:** [GitHub Issues](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/issues)
- **Discussions:** [GitHub Discussions](https://github.com/Fr1ngg/remnawave-bedolaga-telegram-bot/discussions)

### 📚 Полезные ссылки

- [📖 Документация Remnawave](https://docs.remna.st)
- [🤖 Создание Telegram бота](https://t.me/BotFather)
- [🐳 Docker документация](https://docs.docker.com)
- [🐘 PostgreSQL документация](https://www.postgresql.org/docs)

---

## 📄 Лицензия

Проект распространяется под лицензией **MIT**. Подробности в файле [LICENSE](LICENSE).

---

<div align="center">

### 🌟 Понравился проект? Поставьте звезду!

[![Star History Chart](https://api.star-history.com/svg?repos=Fr1ngg/remnawave-bedolaga-telegram-bot&type=Date)](https://star-history.com/#Fr1ngg/remnawave-bedolaga-telegram-bot&Date)

---

**💝 Создано с любовью для Remnawave сообщества**

*Автор не является профессиональным разработчиком, но прикладывает все усилия для создания удобного бота для ваших сервисов* 💪

[🔝 Вернуться наверх](#-remnawave-bedolaga-bot)

</div>
