# Интерактивное развертывание Zabbix Server с HTTPS

[![Ansible](https://img.shields.io/badge/Ansible-2.9+-blue.svg)](https://www.ansible.com/)
[![Docker](https://img.shields.io/badge/Docker-24.0+-blue.svg)](https://www.docker.com/)
[![Zabbix](https://img.shields.io/badge/Zabbix-7.0-red.svg)](https://www.zabbix.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Описание

Автоматизированное развертывание Zabbix Server 7.0 с HTTPS на Ubuntu 24.04. Полностью интерактивный процесс — все данные вводятся при запуске.

## 🚀 ИНСТРУКЦИЯ ПО ЗАПУСКУ

```bash
# 1. Установите Ansible и зависимости
sudo apt update && sudo apt install ansible -y
ansible-galaxy collection install community.docker

# 2. Склонируйте репозиторий
git clone https://github.com/antonpochinkin-bit/zabbix-ansible-deploy.git
cd zabbix-ansible-deploy

# 3. ЗАПУСТИТЕ РАЗВЕРТЫВАНИЕ (самая важная команда!)
ansible-playbook zabbix-deploy.yml
