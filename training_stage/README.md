# Решения заданий интерактивного тренажера по SQL
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
