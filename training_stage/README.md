 # Решения упражнений по SQL
Упражнения на оператор SELECT: обучающий этап

Ссылка на задания SQL тренажёра:  
[https://www.sql-ex.ru/](https://www.sql-ex.ru/)

**Задание: 1** (Serge I: 2002-09-30)\
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

**Задание 2:** (Serge I: 2002-09-21)\
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

**Задание 3:** (Serge I: 2002-09-30)\
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

**Задание 4:** (Serge I: 2002-09-21)\
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

**Задание 5:** (Serge I: 2002-09-30)\
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

**Задание 6:** (Serge I: 2002-10-28)\
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

**Задание 7:** (Serge I: 2002-11-02)\
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

**Задание 8:** (Serge I: 2003-02-03)\
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

**Задание 9:** (Serge I: 2002-11-02)\
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

**Задание 10:** (Serge I: 2002-09-23)\
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

**Задание 11:** (Serge I: 2002-11-02)\
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

**Задание 12:** (Serge I: 2002-11-02)\
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

**Задание 13:** (Serge I: 2002-11-02)\
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

**Задание 14:** (Serge I: 2002-11-05)\
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

**Задание 15:** (Serge I: 2003-02-03)\
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

**Задание 16:** (Serge I: 2003-02-03)\
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

**Задание 17:** (Serge I: 2003-02-03)\
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

**Задание 18:** (Serge I: 2003-02-03)\
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

**Задание 19:** (Serge I: 2003-02-13)\
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

**Задание 20:** (Serge I: 2003-02-13)\
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

**Задание 21:** (Serge I: 2003-02-13)\
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

**Задание 22:** (Serge I: 2003-02-13)\
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

**Задание 23:** (Serge I: 2003-02-14)\
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

**Задание 24:** (Serge I: 2003-02-03)\
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

**Задание 25:** (Serge I: 2003-02-14)\
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

**Задание 26:** (Serge I: 2003-02-14)\
Найдите среднюю цену ПК и ПК-блокнотов, выпущенных производителем A (латинская буква).\
Вывести: одна общая средняя цена.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=26)

<details><summary>Решение</summary>

```sql
SELECT
  AVG(price) 
FROM 
  (
    SELECT
      code, 
      price, 
      laptop.model, 
      ram, 
      hd 
    FROM 
      laptop 
    WHERE 
      model IN (
        SELECT 
          model 
        FROM 
          product 
        WHERE 
          maker = 'A'
      ) 
    UNION 
    SELECT 
      code, 
      price, 
      pc.model, 
      ram, 
      hd 
    FROM 
      pc 
    WHERE 
      model IN (
        SELECT 
          model 
        FROM 
          product 
        WHERE 
          maker = 'A'
      )
  ) AS a
```

</details>

**Задание 27:** (Serge I: 2003-02-03)\
Найдите средний размер диска ПК каждого из тех производителей, которые выпускают и принтеры.\
Вывести: maker, средний размер HD.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=27)

<details><summary>Решение</summary>

```sql
SELECT 
  product.maker, 
  AVG(pc.hd) AS Avg_hd 
FROM 
  product, 
  pc 
WHERE 
  product.model = pc.model 
  AND product.maker IN (
    SELECT 
      DISTINCT maker 
    FROM 
      product 
    WHERE 
      product.type = 'printer'
  ) 
GROUP BY 
  maker
```

</details>

**Задание 28:** (Serge I: 2012-05-04)\
Используя таблицу Product, определить количество производителей, выпускающих по одной модели.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=28)

<details><summary>Решение</summary>

```sql
SELECT 
  COUNT(maker) AS qty 
FROM 
  product 
WHERE 
  maker IN (
    SELECT 
      maker 
    FROM 
      product 
    GROUP BY 
      maker 
    HAVING 
      COUNT(model) = 1
  )
```

</details>

**Задание 29:** (Serge I: 2003-02-14)\
В предположении, что приход и расход денег на каждом пункте приема фиксируется не чаще одного раза в день [т.е. первичный ключ (пункт, дата)], написать запрос с выходными данными (пункт, дата, приход, расход). Использовать таблицы Income_o и Outcome_o.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=29)

<details><summary>Решение</summary>

```sql
SELECT 
  t1.point, 
  t1.date, 
  inc, 
  out 
FROM 
  Income_o t1 
  LEFT JOIN Outcome_o t2 ON t1.point = t2.point 
  AND t1.date = t2.date 
UNION 
SELECT 
  t2.point, 
  t2.date, 
  inc, 
  out 
FROM 
  Income_o t1 
  RIGHT JOIN Outcome_o t2 ON t1.point = t2.point 
  AND t1.date = t2.date
```

</details>

**Задание 30:** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание 31:** (Serge I: 2002-10-22)\
Для классов кораблей, калибр орудий которых не менее 16 дюймов, укажите класс и страну.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=31)

<details><summary>Решение</summary>

```sql
SELECT 
  DISTINCT class, 
  country 
FROM 
  Classes 
WHERE 
  bore >= 16
```

</details>

**Задание 32:** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание 33:** (Serge I: 2002-11-02)\
Укажите корабли, потопленные в сражениях в Северной Атлантике (North Atlantic).\
Вывод: ship.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=33)

<details><summary>Решение</summary>

```sql
SELECT 
  ship 
FROM 
  Outcomes 
WHERE 
  battle = 'North Atlantic' 
  AND result = 'sunk'
```

</details>

**Задание 34:** (Serge I: 2002-11-04)\
По Вашингтонскому международному договору от начала 1922 г. запрещалось строить линейные корабли водоизмещением более 35 тыс.тонн. Укажите корабли, нарушившие этот договор (учитывать только корабли c известным годом спуска на воду).\
Вывести названия кораблей.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=34)

<details><summary>Решение</summary>

```sql
SELECT 
  DISTINCT name 
FROM 
  Ships s 
  JOIN Classes c ON s.class = c.class 
WHERE 
  displacement > 35000 
  AND launched >= 1922 
  AND type = 'bb'
```

</details>

**Задание 35:** (qwrqwr: 2012-11-23)\
В таблице Product найти модели, которые состоят только из цифр или только из латинских букв (A-Z, без учета регистра).\
Вывод: номер модели, тип модели.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=35)

<details><summary>Решение</summary>

```sql
SELECT 
  model, 
  type 
FROM 
  product 
WHERE 
  model NOT LIKE '%[^0-9]%' 
  OR upper(model) NOT LIKE '%[^A-Z]%'
```

</details>

**Задание 36:** (Serge I: 2003-02-17)\
Перечислите названия головных кораблей, имеющихся в базе данных (учесть корабли в Outcomes).\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=36)

<details><summary>Решение</summary>

```sql
SELECT 
  name 
FROM 
  Ships 
WHERE 
  name = class 
UNION 
SELECT 
  ship AS name 
FROM 
  Outcomes 
  JOIN Classes ON Outcomes.ship = Classes.class
```

</details>

**Задание 37:** (Serge I: 2003-02-17)\
Найдите классы, в которые входит только один корабль из базы данных (учесть также корабли в Outcomes).\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=37)

<details><summary>Решение</summary>

```sql
SELECT 
  c.class 
FROM 
  Classes c 
  LEFT JOIN (
    SELECT 
      class, 
      name 
    FROM 
      Ships 
    UNION 
    SELECT 
      Classes.class AS class, 
      Outcomes.ship AS name 
    FROM 
      Outcomes 
      JOIN Classes ON Outcomes.ship = Classes.class
  ) AS s ON c.class = s.class 
GROUP BY 
  c.class 
HAVING 
  COUNT(s.name)= 1
```

</details>

**Задание 38:** (Serge I: 2003-02-19)\
Найдите страны, имевшие когда-либо классы обычных боевых кораблей ('bb') и имевшие когда-либо классы крейсеров ('bc').\
[(сайт)]()

<details><summary>Решение</summary>

```sql
SELECT 
  country 
FROM 
  Classes 
GROUP BY 
  country 
HAVING 
  COUNT(DISTINCT type) > 1
```

</details>

**Задание 39:** (Serge I: 2003-02-14)\
Найдите корабли, `сохранившиеся для будущих сражений`; т.е. выведенные из строя в одной битве (damaged), они участвовали в другой, произошедшей позже.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=39)

<details><summary>Решение</summary>

```sql
SELECT 
  DISTINCT o.ship 
FROM 
  Outcomes o, 
  Battles b 
WHERE 
  o.battle = b.name 
  AND o.ship IN (
    SELECT 
      o1.ship 
    FROM 
      Outcomes o1, 
      Battles b1 
    WHERE 
      o1.battle = b1.name 
      AND o1.result = 'damaged' 
      AND b.date > b1.date
  )
```

</details>

**Задание 40:** (Serge I: 2012-04-20)\
Найти производителей, которые выпускают более одной модели, при этом все выпускаемые производителем модели являются продуктами одного типа.
Вывести: maker, type\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=40)

<details><summary>Решение</summary>

```sql
SELECT 
  maker, 
  MAX(type) AS type 
FROM 
  product 
GROUP BY 
  maker 
HAVING 
  COUNT(model) > 1 
  AND COUNT(DISTINCT type) = 1
```

</details>

**Задание 41:** (Serge I: 2019-05-31)\
Для каждого производителя, у которого присутствуют модели хотя бы в одной из таблиц PC, Laptop или Printer,
определить максимальную цену на его продукцию.\
Вывод: имя производителя, если среди цен на продукцию данного производителя присутствует NULL, то выводить для этого производителя NULL,
иначе максимальную цену.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=41)

<details><summary>Решение</summary>

```sql
WITH subquery AS (
  SELECT 
    maker, 
    price 
  FROM 
    product p 
    JOIN laptop l ON p.model = l.model 
  UNION 
  SELECT 
    maker, 
    price 
  FROM 
    product p 
    JOIN printer pr ON p.model = pr.model 
  UNION 
  SELECT 
    maker, 
    price 
  FROM 
    product p 
    JOIN pc ON p.model = pc.model
) 
SELECT 
  DISTINCT maker, 
  CASE WHEN maker IN (
    SELECT 
      DISTINCT maker 
    FROM 
      subquery 
    WHERE 
      price IS NULL
  ) THEN NULL ELSE MAX(price) END price 
FROM 
  subquery 
GROUP BY 
  maker
```

</details>

**Задание 42:** (Serge I: 2002-11-05)\
Найдите названия кораблей, потопленных в сражениях, и название сражения, в котором они были потоплены.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=42)

<details><summary>Решение</summary>

```sql
SELECT 
  ship, 
  battle 
FROM 
  Outcomes o 
  JOIN Battles b ON o.battle = b.name 
WHERE 
  result = 'sunk'
```

</details>

**Задание 43:**  (qwrqwr: 2011-10-28)\
Укажите сражения, которые произошли в годы, не совпадающие ни с одним из годов спуска кораблей на воду.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=43)

<details><summary>Решение</summary>

```sql
SELECT 
  name 
FROM 
  Battles 
WHERE 
  DATEPART(year, date) NOT IN (
    SELECT 
      launched 
    FROM 
      Ships 
    WHERE 
      launched IS NOT NULL
  )
```

</details>

**Задание 44:** (Serge I: 2002-12-04)\
Найдите названия всех кораблей в базе данных, начинающихся с буквы R.\
[(сайт)](https://www.sql-ex.ru/learn_exercises.php?LN=44)

<details><summary>Решение</summary>

```sql
SELECT 
  r.name 
FROM 
  (
    SELECT 
      Ships.name 
    FROM 
      Ships 
    UNION 
    SELECT 
      Outcomes.ship AS name 
    FROM 
      Outcomes
  ) AS r 
WHERE 
  r.name LIKE 'R%'
```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>

**Задание :** \
[(сайт)]()

<details><summary>Решение</summary>

```sql

```

</details>











