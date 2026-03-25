# off-update.sh

Скрипт для полного отключения автоматических обновлений на Debian/Ubuntu системах.

Подходит для production-серверов, где любые автообновления могут привести к сбоям или рестартам сервисов.

---

## ⚠️ Важно

Скрипт полностью отключает автоматические обновления, включая:
- unattended-upgrades
- APT timers (apt-daily, apt-daily-upgrade)
- snap auto-refresh

После этого система НЕ будет обновляться автоматически.

Обязательно настройте процесс ручных обновлений (CI/CD, Ansible или вручную).

---

## 🚀 Быстрый запуск (one-liner)

    curl -fsSL https://raw.githubusercontent.com/zaycevmain/off-update/main/off-update.sh | sudo sh

---

## ✅ Рекомендуемый способ (production)

Скачать, проверить и запустить:

    curl -fLO https://raw.githubusercontent.com/zaycevmain/off-update/main/off-update.sh
    chmod +x off-update.sh
    less off-update.sh
    sudo ./off-update.sh

---

## 📦 Что делает скрипт

- Останавливает и отключает:
  - unattended-upgrades
  - apt-daily.timer
  - apt-daily-upgrade.timer
- Маскирует службы (чтобы их нельзя было случайно включить)
- Отключает автообновления APT через конфиг
- Удаляет пакет unattended-upgrades
- Отключает auto-refresh для snap
- Проверяет статус таймеров и служб

---

## 🔧 Требования

- Debian / Ubuntu
- root или sudo доступ
- установлен curl или wget

---

## 🔄 Ручное обновление (рекомендуется)

После отключения автообновлений используйте:

    sudo apt update && sudo apt upgrade

Рекомендуется выполнять:
- регулярно (например, раз в неделю)
- через CI/CD или automation

---

## ❗ Отказ от ответственности

Вы используете скрипт на свой страх и риск.

Отключение обновлений может привести к:
- уязвимостям безопасности
- устаревшим пакетам

---

## 🧠 Рекомендации

Для production окружений:
- используйте staging перед обновлением
- автоматизируйте обновления через CI/CD
- отслеживайте security advisories

---

## 📄 Лицензия

MIT
