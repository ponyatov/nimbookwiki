# Makefile
## использование утилиты GNU `make`

```make
# текущий каталог
CWD     = $(CURDIR)
# имя пакета
MODULE  = $(notdir $(CWD))

# дата (для .zip)
NOW     = $(shell date +%d%m%y)
# версия сборки (короткий git hash)
REL     = $(shell git rev-parse --short=4 HEAD)

```
