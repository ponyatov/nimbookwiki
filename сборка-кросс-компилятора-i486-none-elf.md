# сборка кросс-компилятора `i486-none-elf`

```sh
~$ git clone -o gh https://github.com/ponyatov/nimos ; cd nimos
~/nimos$ make cross
```

**Целевая архитектура** задается в нескольких файлах, пока жёстко под i486 PC (как максимально совместимый с любым x86 ПК), но в потенциале набор платформ может быть расширен:

```make
HW = qemu386
# include hw/$(HW).mk
CPU = i486
# include cpu/$(CPU).mk
ARCH = i386
# include arch/$(ARCH).mk
TARGET = $(CPU)-elf
```
