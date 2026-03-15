# Интерактивное развертывание Zabbix Server с HTTPS

[![Ansible](https://img.shields.io/badge/Ansible-2.9+-blue.svg)](https://www.ansible.com/)
[![Docker](https://img.shields.io/badge/Docker-24.0+-blue.svg)](https://www.docker.com/)
[![Zabbix](https://img.shields.io/badge/Zabbix-7.0-red.svg)](https://www.zabbix.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

##  Описание

Этот проект автоматизирует развертывание **Zabbix Server 7.0** с поддержкой **HTTPS** на любом сервере с **Ubuntu 24.04 LTS**. 

**Ключевые возможности:**
-  **Интерактивный ввод** — все данные (IP, пользователь, пароли) вводятся при запуске
-  **Полная автоматизация** — установка Docker, генерация SSL, запуск контейнеров
-  **Мониторинг хоста** — автоматическая установка Zabbix Agent для сбора метрик
-  **Готовый HTTPS** — Nginx reverse proxy с самоподписанным сертификатом

---

##  Состав проекта

| Файл | Описание |
|------|----------|
| `zabbix-deploy.yml` | **Основной плейбук Ansible** (содержит всю логику развертывания) |
| `docker-compose.yml.j2` | **Шаблон Docker Compose** (PostgreSQL, Zabbix Server, Zabbix Web, Nginx) |
| `README.md` | **Документация** |

>  **Важно:** Файл `inventory.ini` не требуется! Плейбук работает полностью интерактивно.

---

##  Предварительные требования

### На вашей управляющей машине (где запускается Ansible)
- Любая ОС с поддержкой Ansible (Linux, macOS, WSL)
- Установленный Git

### На целевом сервере
- **Ubuntu 24.04 LTS** (чистая установка)
- SSH-доступ с пользователем, имеющим права sudo
- Порты **80** и **443** открыты (проверьте firewall и настройки VirtualBox)

---

##  ПОШАГОВАЯ ИНСТРУКЦИЯ ПО ЗАПУСКУ

### Шаг 1: Подготовка управляющей машины

Откройте терминал на вашем компьютере и выполните:

```bash
# Установка Ansible
sudo apt update && sudo apt install ansible -y

# Установка коллекции для Docker
ansible-galaxy collection install community.docker
ansible-galaxy collection install community.docker

# 2. Склонируйте репозиторий
git clone https://github.com/antonpochinkin-bit/zabbix-ansible-deploy.git
cd zabbix-ansible-deploy

# 3. ЗАПУСТИТЕ РАЗВЕРТЫВАНИЕ (самая важная команда!)
ansible-playbook zabbix-deploy.yml
