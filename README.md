# Интерактивное развертывание Zabbix Server

##  Описание

Этот проект позволяет развернуть Zabbix Server на любом Ubuntu сервере **полностью интерактивно**.

**Все данные вводятся при запуске плейбука:**
- IP адрес сервера
- Имя пользователя SSH
- SSH пароль
- SUDO пароль
- Пароль для PostgreSQL
- Пароль для Admin в Zabbix

---

##  Состав проекта

- `zabbix-deploy.yml` - основной интерактивный плейбук
- `docker-compose.yml.j2` - шаблон для контейнеров
- `README.md` - инструкция

**Файл inventory.ini НЕ НУЖЕН!**

---

##  Подготовка

### На управляющей машине:

```bash
# Установка Ansible
sudo apt update && sudo apt install ansible -y

# Установка коллекции для Docker
ansible-galaxy collection install community.docker

# Создание директории проекта
mkdir ~/zabbix-deploy
cd ~/zabbix-deploy

# Создайте файлы zabbix-deploy.yml и docker-compose.yml.j2
# (скопируйте содержимое из проекта)