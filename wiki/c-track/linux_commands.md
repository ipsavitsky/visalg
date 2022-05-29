# Как пользоваться командной строкой Линукса

## Перемещение

Ваше приглашение терминала показывает директорию в которой вы сейчас находитесь. Например,

```bash
ilyasavitsky@pop-os:~/visalg$ 
```

показывает что я нахожусь в директории `~` (специальное обозначение домашней директории). Для того чтобы посмотреть что лежит в текущей директории я могу использовать команду `ls` (`l`i`s`t):

```bash
ilyasavitsky@pop-os:~/test$ ls
cool_directory  helloworld.c
```

В данном тексте не видно, но `cool_directory` это директория. Чтобы в нее перейти - можно использовать команду `cd` (`c`hange `d`irectory):

```bash
ilyasavitsky@pop-os:~/test$ cd cool_directory/
```

Теперь я нахожусь в директории `cool_directory`

```bash
ilyasavitsky@pop-os:~/test/cool_directory$
```

Так же посмотреть текущее местоположение можно при поомщи команды `pwd` (`p`resent `w`orking `d`irectory):

```bash
ilyasavitsky@pop-os:~/test/cool_directory$ pwd
/home/ilyasavitsky/test/cool_directory
```

Для перехода "на уровень выше" можно использовать обращение `..`. Выйдем из `cool_directory` обратно в `test`:

```bash
ilyasavitsky@pop-os:~/test/cool_directory$ cd ..
ilyasavitsky@pop-os:~/test$ pwd
/home/ilyasavitsky/test
```

## Манипулирования разными сущностями

На самом деле тут должна быть манипуляция с файлами потому что все что есть в линуксе это файл - даже директории :)

Чтобы создать директорию можно использовать команду `mkdir` (`m`a`k`e `dir`ectory). Создадим директорию `another_directory` и перейдем в неё:

```bash
ilyasavitsky@pop-os:~/test$ mkdir another_directory
ilyasavitsky@pop-os:~/test$ cd another_directory/
```

Для того чтобы создать файл можно использовать команду `touch`. Создадим с ее помощью файл `main.c` и проверим что он существует при помощи `ls`:

```bash
ilyasavitsky@pop-os:~/test/another_directory$ touch main.c
ilyasavitsky@pop-os:~/test/another_directory$ ls
main.c
```

Заметим, что такое создаие не отличается от аналогичного в `Visual Studio Code`. Но теперь мы решили что этот файл нам не нужен и мы хотим удалить его. Сделаем это при помощи `rm` (`r`e`m`ove)

```bash
ilyasavitsky@pop-os:~/test/another_directory$ ls
main.c
ilyasavitsky@pop-os:~/test/another_directory$ rm main.c 
ilyasavitsky@pop-os:~/test/another_directory$ ls
ilyasavitsky@pop-os:~/test/another_directory$
```

И вправду исчез. В целях этого туториала верну этот файл при помощи `touch main.c` на место и вернусь на директорию выше при помощи `cd ..`.

Попробуем удалить нашу директорию `another_directory`. Делается это при помощи `rmdir`

```bash
ilyasavitsky@pop-os:~/test$ rmdir another_directory/
rmdir: не удалось удалить 'another_directory/': Каталог не пуст
ilyasavitsky@pop-os:~/test$ 
```

Не вышло! Почему? Потому что мы не можем удалить директорию, которая не пуста. Для этого нужно перейти в неё и выполнить команду `rm` на все файлы. Или мы можем сделать сказать программе `rm` зайти в директорию и удалить все внутри, после чего удалить свму директорию. Делается это следующим образом:

```bash
ilyasavitsky@pop-os:~/test$ rm -rf another_directory/
ilyasavitsky@pop-os:~/test$ ls
cool_directory  helloworld.c
ilyasavitsky@pop-os:~/test$ 
```

Удалилось! Победа! `-rf` это флаги команды и сами из себя представляют дополнительные настройки команды. `-r` означает рекурсивно заходить в директории. `-f` означает что при наличии подкаталогов они тоже будут удалены.

Посмотреть наличие из начение флагов можно всегда при помощи утилиты `man` (`man`ual)

```bash
ilyasavitsky@pop-os:~/test$ man rm
```

## Компиляция и запуск

Пусть в файле `helloworld.c` лежит христоматийный пример. Чтобы из консоли посмотреть содержимое файла можно воспользоваться утилитой `cat` (`cat`enate, с кошками эта команда имеет мало общего :) ):

```bash
ilyasavitsky@pop-os:~/test$ cat helloworld.c 
#include <stdio.h>

int main(){
    puts("Hello world\n");
    return 0;
}
ilyasavitsky@pop-os:~/test$ 

```

Программа на Си компилируется компилятором (спасибо, Капитан Очевидность). Их много разных, но тут ради примера воспользуемся самым простым из них - `gcc`.

```bash
ilyasavitsky@pop-os:~/test$ gcc helloworld.c 
ilyasavitsky@pop-os:~/test$ ls
a.out  cool_directory  helloworld.c
ilyasavitsky@pop-os:~/test$ 
```

Заметим, что у нас появился новый файл - `a.out`. Это исполняемый файл, который собрал `gcc`. `a.out` это дефолтное название. Скомпилировать с каким-то конкретным именем можно, указав имя при помощи флагов. Понять как это делается остается упражнением для читателя. Чтобы запустить исполняемый файл достаточно указать полный путь к нему. Вспоминаем про удобный способ адресации текущей директории. Итого, чтобы запустить наш файл достаточно написать

```bash
ilyasavitsky@pop-os:~/test$ ./a.out 
Hello world
ilyasavitsky@pop-os:~/test$ 
```

Ура! Программа запустилась! Победа!

## Референс

- `ls` - посмотреть что в текущей директории
- `cd` - перейти в другую директорию
- `pwd` - посмотреть путь к текущей директории
- `mkdir` - создать директорию
- `rmdir` - удалить директорию (но только пустую)
- `touch` - создать файл
- `rm` - удалить файл
- `man` - посмотерть документацию команды
- `cat` - посмотреть содержимое файла
- `gcc` - компилятор языка Си

Читателю на самостоятельное обучение остаются команды `mv` и `cp`. Можно при помощи `man`.

- `~` - отсылка на домашнюю директорию. Обычно в *nix `/home/<имя пользователя>`
- `.` - отсылка на текущую директорию
- `..` - отсылка на родительскую директорию

Читателю на самостоятельное обучние остается разобраться что такое `*`.
