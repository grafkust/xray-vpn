# Скрипт для лёгкой установки и настройки ядра X-ray без графического интерфейса

Скрипт предназначен для автоматической установки ядра X-ray на сервер.
Создаст конфигурационные и исполняемые файлы для удобного управления.

## Полезные ссылки
- [GitHub проекта X-ray Core](https://github.com/XTLS/Xray-core)
- [Официальная документация на русском](https://xtls.github.io/ru/)

## Как пользоваться скриптом
Команда для скачивания и запуска `xray-install`:
```sh
wget -qO- https://raw.githubusercontent.com/grafkust/xray-vpn/refs/heads/master/xray-install | bash
```

## Команды управления
В домашней папке пользователя будет создан файл `help` — в нём содержатся подсказки с описанием команд.

**Основные команды**
- `cat help` - открыть help файл для просмотра
- `nano $HOME/help` - открыть help файл для редактирования
- `nano /usr/local/bin/fileName` - Открыть исполняемый файл для редактирования
- `mainuser` - Вывести ссылку и QR-код для подключения основного пользователя
- `sharelink` - Создать ссылку для подключения существующего пользователя
- `config` - открывает файл с конфигурацией
- `userlist` - Вывести список всех клиентов
- `newuser` - Создать нового пользователя
- `restart` - перезагружает ядро Xray
- `rmuser` - Удалить пользователя


## Как дополнить скрипт
### Создание исполняемого файла
```
touch /usr/local/bin/fileName

cat << 'EOF' > /usr/local/bin/fileName
#!/bin/bash
...
EOF

chmod +x /usr/local/bin/fileName
```
**Пояснения:**
- `touch` создает пустой файл в указанной директории с нужным именем
- `cat << 'EOF' ... EOF` - heredoc. Позволяет вставить в файл многострочный текст.
- `> /usr/local/bin/fileName` указывает, что вывод heredoc нужно записать в указанный после `>` файл (перезапишет файл, если он уже есть).
- `#!/bin/bash` — shebang. Указывает путь до интерпретатора, который будет исполнять скрипт. В данном случае `/bin/bash`. Можно указать другой интерпретатор `python, Node.js`, если он установлен в системе.
- `chmod +x` делает указанный файл исполняемым. Теперь его можно запускать через команду `fileName`, если он лежит в папке, которая есть в переменной окружения `$PATH` (`/usr/local/bin` находится там по-умолчанию).

## Удаление VPN с сервера
```sh
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ remove
rm /usr/local/etc/xray/config.json
rm /usr/local/etc/xray/.keys
rm /usr/local/bin/userlist
rm /usr/local/bin/mainuser
rm /usr/local/bin/newuser
rm /usr/local/bin/rmuser
rm /usr/local/bin/sharelink
```

## Клиенты для подключения
- [v2rayN](https://github.com/2dust/v2rayN) - Windows
- [v2rayNG](https://github.com/2dust/v2rayNG) - Android
- [Nekoray](https://github.com/MatsuriDayo/nekoray) - Linux
- [V2rayU](https://github.com/yanue/V2rayU) - macOS arm64 & x64
- [Streisand](https://apps.apple.com/app/streisand/id6450534064) - iOS & macOS arm64