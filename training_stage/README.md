# Решения упражнений по SQL
Упражнения на оператор SELECT: обучающий этап

Ссылка на задания SQL тренажёра:  
[https://sql-academy.org/ru/trainer](https://www.sql-ex.ru/learn_exercises.php)

Задание: 1 (Serge I: 2002-09-30)\
Найдите номер модели, скорость и размер жесткого диска для всех ПК стоимостью менее 500 дол.\
Вывести: model, speed и hd.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=1)

<details><summary>Решение</summary>

```sql
SELECT 
  model, speed, hd 
FROM 
  pc
WHERE
  price < 500;
```

</details>

Задание 2: (Serge I: 2002-09-21)\
Найдите производителей принтеров.\
Вывести: maker\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=2)

<details><summary>Решение</summary>

```sql
SELECT 
  DISTINCT maker 
FROM 
  Product
WHERE
  type = 'printer';
```

</details>

Задание 3: (Serge I: 2002-09-30)\
Найдите номер модели, объем памяти и размеры экранов ПК-блокнотов, цена которых превышает 1000 дол.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=3)

<details><summary>Решение</summary>

```sql
SELECT 
  model, ram, screen 
FROM 
  laptop
WHERE
  price > 1000;
```

</details>

Задание 4: (Serge I: 2002-09-21)\
Найдите все записи таблицы Printer для цветных принтеров.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=4)

<details><summary>Решение</summary>

```sql
SELECT
  * 
FROM
  printer
WHERE
  color = 'y';
```

</details>

Задание 5: (Serge I: 2002-09-30)\
Найдите номер модели, скорость и размер жесткого диска ПК, имеющих 12x или 24x CD и цену менее 600 дол.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=5)

<details><summary>Решение</summary>

```sql
SELECT
  model, speed, hd
FROM
  pc
WHERE
  cd IN ('12x', '24x') AND price < 600;
```

</details>

Задание 6: (Serge I: 2002-10-28)\
Для каждого производителя, выпускающего ПК-блокноты c объёмом жесткого диска не менее 10 Гбайт, найти скорости таких ПК-блокнотов.\
Вывод: производитель, скорость.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=6)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT maker, speed
FROM
  laptop
  JOIN product ON laptop.model = product.model
WHERE
  hd >= 10 AND type = 'laptop';
```

</details>

Задание 7: (Serge I: 2002-11-02)\
Найдите номера моделей и цены всех имеющихся в продаже продуктов (любого типа) производителя B (латинская буква).\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=7)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT laptop.model, price
FROM
  laptop
  JOIN product ON laptop.model = product.model
WHERE
  maker = 'B'
UNION
SELECT
  DISTINCT printer.model, price
FROM
  printer
  JOIN product ON printer.model = product.model
WHERE
  maker = 'B'
UNION
SELECT
  DISTINCT pc.model, price
FROM
  pc
  JOIN product ON pc.model = product.model
WHERE
  maker = 'B';
```

</details>

Задание 8: (Serge I: 2003-02-03)\
Найдите производителя, выпускающего ПК, но не ПК-блокноты.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=8)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT maker
FROM
  product
WHERE
  type = 'PC'
EXCEPT
SELECT
  DISTINCT maker
FROM
  product
WHERE
  type = 'laptop';
```

</details>

Задание 9: (Serge I: 2002-11-02)\
Найдите производителей ПК с процессором не менее 450 Мгц.\
Вывести: Maker\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=9)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT maker
FROM
  pc
  JOIN product ON pc.model = product.model
WHERE
  speed >= 450;
```

</details>

Задание 10: (Serge I: 2002-09-23)\
Найдите модели принтеров, имеющих самую высокую цену.\
Вывести: model, price\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=10)

<details><summary>Решение</summary>

```sql
SELECT
  printer.model, price
FROM
  printer
  JOIN product ON printer.model = product.model
WHERE
  price IN (
            SELECT
              MAX(price)
            FROM
              printer)
ORDER BY
  price DESC;
```

</details>

Задание 11: 




