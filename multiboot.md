# `multiboot` загрузчик

`src/multiboot.S`

В примере stand-alone проекта `nimkernel` предоставлен **минимальный загрузчик для i386**, подключение которого в начало вашей прошивки сделает ёё загружаемой любым загрузчиком -- [[syslinux]], [[GRUB]], или `qemu -kernel firmware.elf`

```make
src/multiboot.S:
	$(WGET) -O $@ https://github.com/dom96/nimkernel/raw/master/boot.s
```
