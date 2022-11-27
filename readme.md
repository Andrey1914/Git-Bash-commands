# Шпаргалка по bash

Шпаргалка основных команд Git Bash, терминала OSX, терминала linux.  

## Суть

Консоль — удобный и быстрый инструмент управления компьютером. Вводим команду текстом, получаем результат или сообщение об ошибке с указанием в чём ошибка.

Работая с консолью, мы всегда «находимся» в какой-то папке (это указано в строке над куйрсором). Если там написано `~`, то мы в папке пользователя (зависит от настроек Windows, чаще всего это `C:/Users/ВАШЕИМЯПОЛЬЗОВАТЕЛЯ/`), если там `/d/projects`, мы в папке `D:/projects`.

## Файловая система

### Просмотр содержимого папки

```bash
pwd                     # выводит текущий путь (сокращение от PRINT WORK DIRECTORY)
ls                      # показать содержимое папки
ls -l                   # отображает расширенную информацию о файлах и папках
ls -a                   # то же, но показывать и скрытые файлы и папки
ls -a -1                # то же, но в один столбец
ls -hF -1 --sort=extension # показать содержимое папки «красиво, в один столбец»
ls build/css            # показать содержимое папки ТЕКУЩАЯ_ПАПКА/build/css
ls /d/projects          # показать содержимое папки D:/projects
```

### Перемещение по файловой системе 

Пользователь всегда находится в какой-то папке, она (или полный путь) всегда показана до области ввода команд. 

```bash

cd projects             # переход в папку projects, которая есть в текущей папке
cd /d/projects          # windows: переход в папку projects, расположенную по адресу D:/projects 
cd /c/Program\ Files    # windows: переход в C/:Program Files 
cd .                    # текущая директория
cd ..                   # переход к родительской папке 
cd ~                    # домашняя директория
cd -                    # переход к последней рабочей папке
```

Чтобы не набирать имя папки целиком, наберите первые пару символов и нажмите <kbd>Tab</kbd> — произойдет автодополнение (если нет двух папок, начинающихся с введенных символов, иначе будут показаны сами эти папки). Справедливо для любой команды.

### Создание папок и файлов

```bash
mkdir project                        # создать папку с именем «project»
mkdir project project/css project/js # создать несколько папок
mkdir -p project/{css,js}            # то же, что выше
touch index.html                     # создать файл
touch index.html css/style.css js/script.js # создать файлы (папки css/ и js/ должны уже существовать)
```

### Копирование файлов

```bash
cp index.html catalog.html # копирование файла index.html в тот же каталог с переименованием в catalog.html
cp index.html old/         # копирование файла index.html в папку old/ (все произойдет в текущей папке)
cp temp/ temp2/ -r         # дублирование каталога
```


### Переименование или перемещение файлов

```bash
mv index.html old              # перемещение файла в папку
mv index.html old/new_name.txt # перемещение файла в папку с переименованием файла
mv order.txt orderNew.txt      # переименовать файл
```


### Удаление папок и файлов

```bash
rm ghost.png             # удалить файл
rm -rf old               # удалить папку и всё из нее
```


## Алиасы

Для команд можно создавать алиасы (синонимы). 
Для этого в папке пользователя (OSX и linux) или в C:/Users/ИМЯ_ПОЛЬЗОВАТЕЛЯ/.bashrc (Windows) нужно вписать строки, наподобие alias pro='cd /d/projects' (одна строка в файле — один алиас)..  

```bash
alias                 # отобразит алиасы, которые уже заданы в системе   
alias c='clear'       # создаст алиас который будет очищать консоль
unalias c             # удалит алиас " c "
unalias -a            # удалит все записанные алиасы
```


### Разные мелочи

Подборка команд, показывающих бОльшую скорость работы с консолью, чем с GUI или просто удобных команд. Многие из них могут быть реализованы различными путями с GUI, что ничуть не умаляет удобства консоли.

```bash
clear                 # очистить консоль
df -h                 # показать статистику использования пространства на дисках
grep -i -n --color 'carousel' index.html css/style.css # найти слово carousel в двух указанных файлах (с игнором регистра), вывести строки с этим словом и номера строк (искомое слово подсветить)
grep word -r project  # найти слово word во всех файлах в папке project
find . -iname '*ind*' # найти в текущей папке (и подпапках) все файлы, имена которых содержат ind и показать списком
ls -a >> file.txt     # записать в file.txt результат вывода команды ls -a
ls src/less/mixins    # показать содержимое папки с указанным путем без перехода в неё
```

