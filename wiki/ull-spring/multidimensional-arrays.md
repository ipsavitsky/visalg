# Многомерные массивы

В нашей многогранной и в общем-то достаточно необъятной жизни бывает даже такое, что хочется, чтобы *элементом* массива был другой *другой массив*. Например, всем понятный случай, когда необходимо что-то рисовать. Картинка в цифровом формате представляет собой *матрицу*, т.е. *двумерный массив* чисел. Аналогично одномерному случаю, двумерные массивы бывают *статические* и *динамические* с точно той же семантикой.

## Статический многомерный массив

```Pascal
var 
  arr: array [1..3, 1..3] of integer; {Матрица 3x3}
begin
  {Заполнение матрицы числами от 1 до 9}
  for i: integer := 1 to 3 do
  begin
    for j := 1 to 3 do
    begin
     arr[i, j] := 3 * (i - 1) + j;
    end;
  end;
  
  {Вывод матрицы на экран}
  for i := 1: integer to 3 do
  begin
    for j := 1 to 3 do
    begin
     write(arr[i, j]);
      write(' ');
    end;
    writeln;
  end;
end.
```

## Динамический многомерный массив

```Pascal
var 
  arr: array of array of integer; {Матрица не заданного на этапе компиляции размера}
  n: integer;
begin
  writeln('Введите размерность матрица:');
  readln(n);
  
  {Выделение памяти}
  setlength(arr, n);
  
  for i: integer := 0 to n - 1 do
  begin
    setlength(arr[i], n);
  end;
  
  {Заполнение матрицы числами от 1 до n^2}
  for i: integer := 0 to n - 1 do {Обратите внимание: нумерация с 0 до n - 1!}
  begin
    for j: integer := 0 to n - 1 do
    begin
     arr[i, j] := (n * i) + j + 1;
    end;
  end;
  
  {Вывод матрицы на экран}
  for i: integer := 0 to n - 1 do
  begin
    for j: integer := 0 to n - 1 do
    begin
     write(arr[i, j]);
      write(' ');
    end;
    writeln;
  end;
  
  {Очистка памяти}
  for i: integer := 0 to n-1 do
  begin
    setlength(arr[i], 0);
  end;
  
  setlength(arr, 0);
  
end.
```

## Задачи

- [Транспонирование матриц](/ull-spring/multidimensional-arrays/transpose)
