# MySQL/MariaDB

Одна из самых распространённых полноценных СУБД, библиотеки для Nim включают биндинги для `libmysql-dev`

* https://nim-lang.org/docs/db_mysql.html

## пример: миграция данных между БД на разных серверах

```nim
# migrate.nimble

description   = "MySQL data migration in Nim lang"

# зависимости

requires "nim >= 1.2.0"
# not requires "db_mysql" в составе библиотеки

```
