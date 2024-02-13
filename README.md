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
