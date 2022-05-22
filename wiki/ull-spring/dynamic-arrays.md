
# Динамические массивы

Заметим, что в прошлом примере мы жёстко привязались к размеру массива, указав его *в момент компиляции* (то есть до непосредственного исполнения кода). Бывает такое, что пользователь захочет ввести больше, чем 5 чисел. Тогда есть инструмент спросить у него, сколько элементов он хочет, и выделить массив нужного размера.

Принципиально отличие статических и динамических структур заключается в том, что с первыми работа проще и полностью контролируется программой, а вот размеры вторых вам придется контролировать самим.

Для примера попробуем как раз выделить память на столько чисел, сколько нужно:

```pascal
var 
  arr: array of integer; {Обратите внимание: тут НЕТ индексов, 
                            как было в предыдущем примере}
  i, tmp, num: integer;

begin
  writeln('Сколько чисел вы хотите ввести: ');
  readln(num);
  {Выделение памяти}
  setlength(arr, num);
  {Работа с массивом}
  for i := 1 to num do
  begin
    readln(tmp);
    arr[i] := tmp;
  end;
  
  for i := 1 to num do
  begin
    write('arr[');
    write(i);
    write('] = ');
   writeln(arr[i]);
  end; 
  {Очистка памяти}
  setlength(arr, 0);
end.
```

Обратите внимание: в конце программы стоит очистка памяти. Так делать нужно ***всегда***. Забыть про это -- очень распространённая ошибка, которая во взрослом мире называется *утечкой памяти* (*memory leak*).

## Задачи

- [Строки или массивы символов](/ull-spring/dynamic-arrays/string-or-char-array)
- [Среднее количество осадков](/ull-spring/dynamic-arrays/average-weather)