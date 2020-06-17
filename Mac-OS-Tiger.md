# Mac OS X 10.4 Tiger

[[Mac Mini G4]]

Для компиляции на устройстве требуется версия Xcode 2.5 для PowerPC: файл образа диска `xcode25_8m2558_developerdvd.dmg`

## Установка в эмулятор QEMU

https://github.com/ponyatov/nimbook/tree/master/macG4

```sh
~/nimbook/macG4$ make
```

* https://wiki.qemu.org/Documentation/GuestOperatingSystems/MacOS10.4

```sh
~$ qemu-system-ppc -hda <HD image file> -boot c -netdev user,id=mynet0 -device rtl8139,netdev=mynet0
 -m 512 -device usb-kbd -device usb-mouse -M mac99 -localtime
```
