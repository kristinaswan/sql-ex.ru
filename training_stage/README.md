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

Задание 11: (Serge I: 2002-11-02)\
Найдите среднюю скорость ПК.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=11)

<details><summary>Решение</summary>

```sql
SELECT
  AVG(speed)
FROM
  pc
```

</details>

Задание 12: (Serge I: 2002-11-02)\
Найдите среднюю скорость ПК-блокнотов, цена которых превышает 1000 дол.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=12)

<details><summary>Решение</summary>

```sql
SELECT
  AVG(speed)
FROM
  laptop
WHERE
  price > 1000
```

</details>

Задание 13: (Serge I: 2002-11-02)\
Найдите среднюю скорость ПК, выпущенных производителем A.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=13)

<details><summary>Решение</summary>

```sql
SELECT
  AVG(speed)
FROM
  pc
  JOIN product ON pc.model = product.model
WHERE
  maker = 'A'
```

</details>

Задание 14: (Serge I: 2002-11-05)\
Найдите класс, имя и страну для кораблей из таблицы Ships, имеющих не менее 10 орудий.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=14)

<details><summary>Решение</summary>

```sql
SELECT
  Ships.class, name, country
FROM
  Ships
  JOIN Classes ON Ships.class = Classes.class
WHERE
  numGuns >= 10
```

</details>

Задание 15: (Serge I: 2003-02-03)\
Найдите размеры жестких дисков, совпадающих у двух и более PC.\
Вывести: HD\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=15)

<details><summary>Решение</summary>

```sql
SELECT
  hd
FROM
  pc
GROUP BY
  hd
HAVING
  COUNT(model) >= 2
```

</details>

Задание 16: (Serge I: 2003-02-03)\
Найдите пары моделей PC, имеющих одинаковые скорость и RAM. В результате каждая пара указывается только один раз, т.е. (i,j), но не (j,i), Порядок вывода: модель с большим номером, модель с меньшим номером, скорость и RAM.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=16)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT a.model, b.model, a.speed, a.ram
FROM
  pc AS a, pc AS b
WHERE
  a.speed = b.speed AND a.ram = b.ram AND a.model > b.model
```

</details>

Задание 17: (Serge I: 2003-02-03)\
Найдите модели ПК-блокнотов, скорость которых меньше скорости каждого из ПК.\
Вывести: type, model, speed\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=17)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT product.type, laptop.model, speed
FROM
  product
  JOIN laptop ON product.model = laptop.model
WHERE
  speed < ALL (SELECT speed FROM pc)
```

</details>

Задание 18: (Serge I: 2003-02-03)\
Найдите производителей самых дешевых цветных принтеров.\
Вывести: maker, price\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=18)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT product.maker, printer.price
FROM
  product, printer
WHERE
  product.model = printer.model AND color = 'y' AND price IN (SELECT MIN(price) FROM printer WHERE printer.color = 'y')
```

</details>

Задание 19: (Serge I: 2003-02-13)\
Для каждого производителя, имеющего модели в таблице Laptop, найдите средний размер экрана выпускаемых им ПК-блокнотов.\
Вывести: maker, средний размер экрана.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=19)

<details><summary>Решение</summary>

```sql
SELECT
  maker, AVG(screen)
FROM
  product
  JOIN laptop ON product.model = laptop.model
WHERE
  laptop.model IN (SELECT model FROM product)
GROUP BY
  maker
```

</details>

Задание 20: (Serge I: 2003-02-13)\
Найдите производителей, выпускающих по меньшей мере три различных модели ПК.\
Вывести: Maker, число моделей ПК.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=20)

<details><summary>Решение</summary>

```sql
SELECT
  maker, COUNT(model) AS count_model
FROM
  product
WHERE
  type = 'pc'
GROUP BY
  maker
HAVING
  COUNT(model) > 2
```

</details>

Задание 21: (Serge I: 2003-02-13)\
Найдите максимальную цену ПК, выпускаемых каждым производителем, у которого есть модели в таблице PC.\
Вывести: maker, максимальная цена.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=21)

<details><summary>Решение</summary>

```sql
SELECT
  maker, MAX(price)
FROM
  product
  JOIN pc ON product.model = pc.model
WHERE
  product.model IN (SELECT model FROM pc)
GROUP BY
  maker
```

</details>

Задание 22: (Serge I: 2003-02-13)\
Для каждого значения скорости ПК, превышающего 600 МГц, определите среднюю цену ПК с такой же скоростью.\
Вывести: speed, средняя цена.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=22)

<details><summary>Решение</summary>

```sql
SELECT
  speed, AVG(price)
FROM
  pc
WHERE
  speed > 600
GROUP BY
  speed
```

</details>

Задание 23: (Serge I: 2003-02-14)\
Найдите производителей, которые производили бы как ПК со скоростью не менее 750 МГц, так и ПК-блокноты со скоростью не менее 750 МГц.\
Вывести: Maker\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=23)

<details><summary>Решение</summary>

```sql
SELECT
  maker
FROM
  product
  JOIN pc ON product.model = pc.model
WHERE
  type = 'pc' AND pc.speed >= 750
INTERSECT
SELECT
  maker
FROM
  product
  JOIN laptop ON product.model = laptop.model
WHERE
  type = 'laptop' AND laptop.speed >= 750
```

</details>

Задание 24: (Serge I: 2003-02-03)\
Перечислите номера моделей любых типов, имеющих самую высокую цену по всей имеющейся в базе данных продукции.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=24)

<details><summary>Решение</summary>

```sql
WITH tables AS
(SELECT
  model, price
FROM
  laptop
UNION
SELECT
  model, price
FROM
  printer
UNION
SELECT
  model, price
FROM
  pc)
SELECT
  model
FROM
  tables
WHERE
  price IN (SELECT MAX(price) FROM tables)
```

</details>

Задание 25: (Serge I: 2003-02-14)\
Найдите производителей принтеров, которые производят ПК с наименьшим объемом RAM и с самым быстрым процессором среди всех ПК, имеющих наименьший объем RAM.\
Вывести: Maker\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=25)

<details><summary>Решение</summary>

```sql
SELECT
  DISTINCT maker
FROM
  product
WHERE
  model IN (SELECT model FROM pc WHERE ram = (SELECT MIN(ram) FROM pc) AND speed = (SELECT MAX(speed) FROM pc WHERE ram = (SELECT MIN(ram) FROM pc))) AND maker IN (SELECT maker FROM product WHERE type='printer')
```

</details>

Задание : \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

Задание : \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

Задание : \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

Задание : \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

