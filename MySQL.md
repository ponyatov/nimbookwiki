# MySQL/MariaDB

Одна из самых распространённых полноценных СУБД, библиотеки для Nim включают биндинги для `libmysql-dev`

* https://nim-lang.org/docs/db_mysql.html

## пример: миграция данных между БД на разных серверах

* `migrate.nimble`
```nim
description   = "MySQL data migration in Nim lang"

# зависимости

requires "nim >= 1.2.0"
# not requires "db_mysql" в составе библиотеки
```
* `src/migrate.nim`
```nim
import db_mysql
```
```nim
# БД-источник

const FROM_IP = "192.168.123.45"
const FROM_LOGIN = "user"
const FROM_PSWD = "password"
const FROM_DB = "forecast"
```
```nim
# БД-приёмник

# from djangobully import settings
## пока возможность разбора файла конфигурации на Python проигнорируем

const TO_IP = "127.0.0.1"
const TO_LOGIN = "bully"
const TO_PSWD = "hiddenpassword"
const TO_DB = "bully"
```

