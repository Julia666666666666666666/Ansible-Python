# Ansible-Python

## 1-Установка Python

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
Проверяем, что Python3.12 установился
```
python3.12
```
![image](https://github.com/Julia666666666666666666/Ansible-Python/assets/148867585/4d232560-82dc-4f59-aa99-dc39beb542f5)
