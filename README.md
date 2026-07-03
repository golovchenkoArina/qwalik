
# 1. установка базового по
sudo apt update

sudo apt upgrade -y 
# 2. установка драйверов
Sudo ubuntu-drivers autoinstall
# 3. установка базового набора утилит
sudo apt install -y curl wget git net-tools htop nano vim mc tree
# 4. установка архиватора
sudo apt install -y p7zip-full p7zip-rar
# 5. установка графического редактора gimp
sudo apt install -y gimp
# 6. установка офисного пакета libreoffice
sudo apt install -y libreoffice libreoffice-l10n-ru
# 7.  установка антивирусника
sudo apt install -y clamav clamav-daemon
# 8. установка среды разработки
sudo snap install --classic code 
# 9. установка виртуального принтера
sudo apt update

sudo apt install cups-pdf
# 10. создание директории для пдф файлов
mkdir -p ~/PDF
# 11. тест печати виртуального принтера
**создание текстового файла**

echo "Тест печати. Группа 301ИС-23" > test.txt

**печать через виртуальный принтер**

lp -d PDF test.txt
# 12. создание точки восстановления
sudo apt install -y timeshift

**Создаем точку восстановления**

sudo timeshift --create --comments "Экзамен ПМ.04 - точка восстановления"

**Просмотр созданных точек**

sudo timeshift --list 
# 13. создание группы пользователей
sudo groupadd students

**создание пользователей и добавление их в группы**

sudo adduser student1

sudo usermod -aG students student1
# 14. настройка прав доступа
**создание папки**

mkdir test

**изменить владельца**

sudo chown student1:students test

**выдать права**

chmod 770 test
# 15. настроить аутентификацию и журналирование
**просмотреть журнал**

journalctl

**последние записи**

journalctl -n 20

**просмотр входов пользователей**

last
# 16. проверка совместимости
apt-cache depends gimp

**проверка версии**

gimp --version

# Создание папки для бэкапов:
sudo mkdir -p /backup


# Бэкап системы (tar):
sudo tar -czpf /backup/backup.tar.gz --exclude=/proc --exclude=/sys --exclude=/dev --exclude=/tmp /


# Бэкап через rsync:
sudo rsync -aAXv --exclude={/proc,/sys,/dev,/tmp} / /backup/system/


# Точка восстановления (Timeshift):
sudo timeshift --create --comments "Точка"


# Проверка бэкапов:
ls -lh /backup/


# Размер бэкапа:
du -sh /backup/*

