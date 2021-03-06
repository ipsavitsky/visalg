# Статические массивы

## Вступительное слово

Вспомним юность: мы умеем предоставлять решение задачи поиска максимального элемента в потоке данных (т.е. когда числа вводятся с клавиатуры). Вот же оно:

```Pascal
var 
 i, num, max, tmp : integer;
begin
  writeln('Введите, сколько чисел вы хотите:');
  readln(num);
  for i := 1 to num do
  begin
    if i = 1 then
    begin
      readln(max);
    end;
    else
    begin
      readln(tmp);
      if tmp > max then
      begin
        max := tmp;
      end;
    end;
  end;
  writeln('Максимальное число из введённых равно ');
  writeln(max);
end.
```

Понятно, что с таким инструментом далеко не уедешь. Например, мы можем захотеть вывести все элементы, введённые пользователем, в порядке возрастания.

## Как создаются статические массивы

Поэтому в непростой программистской жизни бывает необходимость создавать *сущность*, которая хранит несколько одинаковых элементов (например, несколько целых чисел). Такая штука называется ***массивом***. Вот пример программы, которая выводит на экран 5 чисел пользователя, которые тот ввёл:

```Pascal
var 
 i, tmp : integer;
 arr : array[1..5] of integer;
begin
  {Заполнение массива числами с экрана}
  for i := 1 to 5 do
  begin
    readln(tmp);
    arr[i] := tmp;
  end;
  {Вывод на экран}
  for i:= 1 to 5 do
  begin
    write('arr[');
    write(i);
    write('] = ');
   writeln(arr[i]);
  end;
end.
```

## Задачи

- [Знакомимся с массивами](/ull-spring/static-arrays/first-try)
- [Добавление элемента](/ull-spring/static-arrays/insert-element)
