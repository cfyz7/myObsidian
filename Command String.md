### `pwd 
проверка текущей дириктории

### `ls
просмотр содержимого директории

### `ls -a 
просмотр скрытых директорий

### `ls -l 
выводит дополнительную информацию

### `cd 
вход в директорию
cd Music

### `cd ..
переход на уровень выше
cd ../..  переход на две директории выше 

### `sudo dpkg -i
установка программы в директории 

### `cat
просмотр содержимого файла 

### `sudo less syslog
`less`  открывает файл и остаётся в этом режиме

### `sudo apt  install neovim 
Устанавливает Вим

### `grep alieses .bashsrc
поиск слова alieses в файле bashsrc

### `создание файла и добавление в файл
echo 'hello' > result
cat result 
hello
echo 'hello' >> result
cat result
hello hello 

### `cat source | grep Dog | uniq | sort
1.  Читается файл source
2.  Входные данные грепаются по подстроке "Dog"
3.  Убираются дубли (в исходном файле две одинаковых строки "Dog")
4.  Входные данные сортируются и выводятся на экран

### `head -n 2(ceil- нижние, -n 2 колличество)
Взять первые две строки

### `touch 
создает файл

### `rm 
удаляет файл

### `rm -R название-папки`
Для удаления папки и ее содержимого (рекурсивное удаление) воспользуйтесь командной rm с опцией -R:  
 
### `mv
переименовывает файл (```mv file renamed-file```)

### `cp
копирует файл (```cp renamed-file renamed-file-copy```)
Для копирования директории нужно добавить флаг `-r`

### `mkdir -p one/two/three
создает вложенные директории

### `rm -r my-dir
удаление директории 

### `rm -rf one
удаление директории с ограниченным доступом 

### `echo $HOME
показывает домашнюю директорию 

### `HOME=/tmp 
меняет домашнюю директорию в текущей сессии

### `export HOME=/tmp
меняет домашнюю директорию.
А также создает новую переменную, если её нет.(export NEW_VAR=/value)

### `Ctrl + R
реверсивный поиск в командах 

### `history 5
показывает пять последних команд

### `id -u nobody
поиск ид-номера пользователя ноубоди

### `echo "Hello, World" | sudo tee config/myfile
создает файл с содержимым в директории судо

### `chmod 511 myfile 
изменение прав пользователей для файла 

### `$ ./helloworld 
запуск программы из директории в которой находишься   

### `Задача на поиск ошибок в определенном файле
grep 'denied wrong password' logs/access.log | sort -r | head -n 5

### `Задача на измненение поля ввода в командной строке
 '> tirion@/usr/src/app$ export PS1="> \u@\W$ "        > tirion@app '
 меняет абсолютный путь на относительный

## `env 
показывает список переменных окружения 


 

