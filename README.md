# Ansible-Python

## 1-Установка Python (ALT)

Для начала нужно установить отдельную В/М и подключить ее к интернету

После устанавливаем утилиту для скачивания файлов из интернета
```
apt-get install wget
```
Далее переходим в папку /tmp/
```
cd /tmp/
```
И скачать файл:
```
wget https://www.python.org/ftp/python/3.12.1/Python-3.12.1.tgz
```
 Распакуем файл
 ```
tar zxvf Python-3.12.1.tgz
```
Скопируем распакованную папку
```
cp -r Python-3.12.1 /usr/local/bin
cd /usr/local/bin/Python-3.12.1/
```
Далее нужно установить пакеты
```
apt-get install zlib-devel libssl-devel libsqlite3-devel libffi-devel gcc
apt-get install pip
```
Добавим параметры для компиляции
```
./configure --prefix=/usr/local --with-ensurepip=install
```
Начинаем компилировать
```
make
make install
```
Удалим за собой весь мусор
```
make clean
cd /
rm -rf /usr/local/bin/Python-3.12.1
```
Проверяем, что Python3.12 установился
```
python3.12
```
![image](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/4d232560-82dc-4f59-aa99-dc39beb542f5)

### 1-Установка Python (Debian)

Для начала нужно установить отдельную В/М и подключить ее к интернету

После устанавливаем утилиту для скачивания файлов из интернета
```
sudo apt install -y python3-venv
```
Загрузим и извлекем исходный код Python
```
cd /tmp/
wget https://www.python.org/ftp/python/3.12.2/Python-3.12.2.tgz
tar -xzvf Python-3.12.2.tgz
cd Python-3.12.2/
```
Теперь установим инструменты сборки. Инструменты сборки включают библиотеки gcc, make, zlib, ssl и другие библиотеки.
```
sudo apt update
sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev
```
Запустим сценарий настройки и включим оптимизацию с учетом профиля (PGO) и оптимизацию времени соединения (LTO). Это может увеличить скорость до 20%.
```
./configure --enable-optimizations
```
Теперь запустите make
```
make -j `nproc`
```
Чтобы просмотреть версию
```
python3.12 -V
```
![image](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/c2497a0c-c4e3-43f7-bfa0-1bb94d14d740)

Чтобы установить версию Python 3.12.2 по умолчанию
```
sudo ln -s /usr/local/bin/python3.12 /usr/local/bin/python
```
## 2-Создание виртуального окружения Python

В домашнем каталоге пользователя создаем папку ansible. Пользователь root
```
mkdir /home/root/ansible
cd /home/root/ansible
```
Создаем виртуальное окружение
```
python3.12 -m venv .env
```
Активируем его
```
source .env/bin/activate
```
Итог

![pic1-1](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/59fed132-8b20-4d9d-b874-9307edb729b6)

## 3-Подключение VSCode по SSH к серверу

Смотрим  в VSCode установленно ли расширение Remote explorer

Если нет расширения, то устанавливаем
![pic1](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/54e2f912-f43c-49fe-876e-792ab9ce95d1)
Нажимаем на плюсик и добавляем свою виртуалку в список SSH подключений
![pic3](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/9d66efaf-8641-4916-83bc-152e61f976fd)

Обнавляем список подключений

![pic4-1](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/2e2d3cae-94e9-49d4-a9fa-391c1d14ad87)

Добавляем папку которая находится на удаленном устройстве

![pic5](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/be94a3a9-b735-4f28-a1db-fb3c29feb075)

![pic6](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/6d80babf-0420-4f92-a440-c136ff7497c5)

Ждем, когда на виртуалку установится VSCode

Открываем папку ansible, если папки не существует, то создаем ее

![pic7](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/4bd3b0d1-fe72-4228-98f3-3cd5c27c2c41)

## 4-Установка ansible

В VSCode откройте терминал. Проверьте что вы находитесь в папке ansible и у вас активированно виртуальное оркужение

![pic1](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/37028953-c58d-4f1f-8939-07dbd3f2e2f3)

Ansible это пакет python. Пакет можно установить при помощи утилиты командной строки pip
```
pip install ansible
```
## 5-Начальная настройка ansible

В папке с витуальным окружением создайте файл ansible.cfg со следующим содержимом
```
[defaults]

inventory = ./hosts.yaml
ask_pass = False
host_key_checking = False
```



