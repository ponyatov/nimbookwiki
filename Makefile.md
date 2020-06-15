# Makefile
## использование утилиты GNU `make`

```make
target: source1 source2 source3
<tab>command
```

|||
|-|-|
|`$@`|`target`|
|`$<`|`source1`|
|`$?`|только изменённые `sourceN`|
|`$^`|все `sourceN`|

* `make` позволяет задать группам shell-комманд имена, запускать их по этому имени, и использовать подстановочные переменные
* главная задача -- запускать группы команд *только для изменённых файлов*, некоторые проекты насчитывают тысячи файлов с исходным кодом, и перезапускать компиляции для всех вместо одного файла вполне может занять несколько часов на *каждое* редактирования кода

```make
# текущий каталог
CWD     = $(CURDIR)
# имя пакета
MODULE  = $(notdir $(CWD))

# дата (для .zip)
NOW     = $(shell date +%d%m%y)
# версия сборки (короткий git hash)
REL     = $(shell git rev-parse --short=4 HEAD)

# сетевые настройки для веб-сервера по умолчанию
IP     ?= 127.0.0.1
PORT   ?= 19999
```

> ВАЖНО: в каждом правиле команды отбиваются **символом табуляции**,
> использование пробелов -- синтаксическая ошибка

```make
# первое правило: по умолчанию, будет использовано при запуске make без параметров
.PHONY: all
all: hello

.PHONY: hello
hello: $(NIMBLE)
	cd $@ ; $< build ; ./$@
```

## минимальная версия

```make
CWD     = $(CURDIR)
MODULE  = $(notdir $(CWD))

.PHONY: all
all: $(MODULE)
	./$^

$(MODULE): $(MODULE).nimble src/$(MODULE).nim Makefile
	nimble build
```

## установка/обновление (на примере Python-проекта)

```make
# установка ПО

.PHONY: install
install: debian $(PIP)
	$(PIP) install    -r requirements.txt
	$(MAKE) requirements.txt

# обновление ПО

.PHONY: update
update: debian $(PIP)
	$(PIP) install -U    pip
	$(PIP) install -U -r requirements.txt
	$(MAKE) requirements.txt

$(PIP) $(PY):
	python3 -m venv .
	$(PIP) install -U pip pylint autopep8
	$(MAKE) requirements.txt

.PHONY: requirements.txt
requirements.txt: $(PIP)
	$< freeze | grep -v 0.0.0 > $@
```
## установка необходимых компонентов операционной системы (дистрибутива)

```
.PHONY: debian
debian:
	sudo apt update
	sudo apt install -u `cat apt.txt`
```

#### `apt.txt` список пакетов необходимых для транслятора Nim

```{file:apt.txt}
git make build-essential
```

#### автоустановка Nim

```make
NIMBLE	= $(HOME)/.nimble/bin/nimble

.PHONY: all
all: hello

.PHONY: hello
hello: $(NIMBLE)
	cd $@ ; $< build ; ./$@

$(NIMBLE):
	curl https://nim-lang.org/choosenim/init.sh -sSf | sh
```
