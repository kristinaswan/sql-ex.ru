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
([сайт])(https://www.sql-ex.ru/learn_exercises.php?LN=3)

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

Задание 4: 


