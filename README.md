# 🚀 Интерактивное развертывание Zabbix Server с HTTPS

[![Ansible](https://img.shields.io/badge/Ansible-2.9+-blue.svg)](https://www.ansible.com/)
[![Docker](https://img.shields.io/badge/Docker-24.0+-blue.svg)](https://www.docker.com/)
[![Zabbix](https://img.shields.io/badge/Zabbix-7.0-red.svg)](https://www.zabbix.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📋 Описание проекта

Этот проект автоматизирует развертывание **Zabbix Server 7.0** с поддержкой **HTTPS** на любом сервере с **Ubuntu 24.04 LTS**. Развертывание происходит полностью интерактивно с использованием Ansible и Docker.

**✨ Ключевые особенности:**
- 🔐 **Полная интерактивность** — все данные (IP, пользователь, пароли) вводятся при запуске, никаких паролей в файлах.
- ⚙️ **Автоматизация** — установка Docker, генерация SSL-сертификатов, запуск контейнеров.
- 🖥️ **Мониторинг хоста** — автоматическая установка и настройка Zabbix Agent для сбора метрик с самого сервера.
- 🌐 **Готовый HTTPS** — настроен Nginx reverse proxy с самоподписанным сертификатом и редиректом с HTTP на HTTPS.

---

## 📁 Состав проекта

| Файл | Назначение |
| :--- | :--- |
| `zabbix-deploy.yml` | **Главный плейбук Ansible.** Содержит всю логику развертывания. |
| `docker-compose.yml.j2` | **Шаблон Docker Compose.** Описывает сервисы: PostgreSQL, Zabbix Server, Zabbix Web, Nginx proxy. |
| `README.md` | **Документация.** То, что вы сейчас читаете. |

> **Важно:** Файл `inventory.ini` **не требуется**, так как плейбук работает в интерактивном режиме.

---

## 🛠 Предварительные требования

### На вашей управляющей машине (где запускается Ansible)
*   Установленный **Ansible** (версия 2.9 или выше).
*   Установленная коллекция **community.docker**.
*   SSH-доступ до целевого сервера.

### На целевом сервере
*   Чистая установка **Ubuntu 24.04 LTS**.
*   SSH-сервер запущен.
*   Пользователь с правами **sudo** (например, `anton`).
*   Порты **80** и **443** должны быть открыты (в настройках firewall и VirtualBox/NAT, если используется).

---

## 🚀 Быстрый старт

### 1. Подготовка управляющей машины
Выполните эти команды на компьютере, с которого будете запускать развертывание:
```bash
# Установка Ansible
sudo apt update && sudo apt install ansible -y

# Установка коллекции для управления Docker через Ansible
ansible-galaxy collection install community.docker
