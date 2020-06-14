# установка на Linux

https://nim-lang.org/install_unix.html

* компилятор устанавливается в домашний каталог пользователя, и не затрагивает системную файловую систему
* для работы нужно добавить пути в `$PATH` и создать пару [[переменных среды|переменные среды]]

```sh
~$ curl https://nim-lang.org/choosenim/init.sh -sSf | sh
```

```
nimtest@debian:~$ curl https://nim-lang.org/choosenim/init.sh -sSf | sh
choosenim-init: Downloading choosenim-0.6.0_linux_amd64
    Prompt: Can choosenim record and send anonymised telemetry data? [y/n]
        ... Anonymous aggregate user analytics allow us to prioritise
        ... fixes and features based on how, where and when people use Nim.
        ... For more details see: https://goo.gl/NzUEPf.
    Answer: y
Downloading Nim 1.2.0 from nim-lang.org
[###############################################   ] 94.72% 752kb/s
 Extracting nim-1.2.0-linux_x64.tar.xz
   Building Nim 1.2.0
  Compiler: Already built
     Tools: Already built
  Installed component 'nim'
  Installed component 'nimble'
  Installed component 'nimgrep'
  Installed component 'nimpretty'
  Installed component 'nimsuggest'
  Installed component 'testament'
   Switched to Nim 1.2.0
choosenim-init: ChooseNim installed in /home/nimtest/.nimble/bin
choosenim-init: You must now ensure that the Nimble bin dir is in your PATH.
choosenim-init: Place the following line in the ~/.profile or ~/.bashrc file.
choosenim-init:     export PATH=/home/nimtest/.nimble/bin:$PATH
```
```sh
~$ echo "export PATH=/home/nimtest/.nimble/bin:\$PATH" >> ~/.setenv
~$ echo ". ~/.setenv" >> ~/.profile
~$ echo ". ~/.setenv" >> ~/.xsesstionrc
```

### обновление

```sh
~$ choosenim update self
```

### [[переменные среды]]

## [[choosenim]]
## [[nimble]]
## [[nimc]]
