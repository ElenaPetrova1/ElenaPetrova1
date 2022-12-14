Решение задач с сайта https://sql-ex.ru

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=1">1 задача</a></h2>
 
```sql
SELECT model, speed, hd   
FROM PC
WHERE price < 500
```
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=2">2 задача</a></h2>

```sql
SELECT DISTINCT maker 
FROM Product
WHERE type = 'Printer'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=3">3 задача</a></h2>

```sql
SELECT model, ram, screen
FROM Laptop
WHERE price > 1000
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=4">4 задача</a></h2>

```sql
SELECT code, model, color, type, price
FROM Printer
WHERE color = 'y'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=5">5 задача</a></h2>

```sql
SELECT model, speed, hd
FROM PC
WHERE ( cd = '12x' OR cd = '24x' ) AND price < 600
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=6">6 задача</a></h2>

```sql
SELECT distinct p.maker as maker, l.speed as speed 
FROM laptop l join product p 
ON l.model = p.model 
WHERE l.hd >= 10
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=7">7 задача</a></h2>

```sql
SELECT DISTINCT pc.model, price 
FROM pc 
JOIN product on pc.model = product.model 
WHERE maker = 'B'
UNION 
SELECT DISTINCT laptop.model, price 
FROM laptop 
JOIN product on laptop.model = product.model 
WHERE maker = 'B'
UNION
SELECT DISTINCT printer.model, price 
FROM printer 
JOIN product on printer.model = product.model 
WHERE maker = 'B'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=8">8 задача</a></h2>

```sql
SELECT maker 
FROM product 
WHERE type = 'pc' 
EXCEPT 
SELECT maker 
FROM product 
WHERE type = 'laptop'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=9">9 задача</a></h2>

```sql
SELECT DISTINCT Maker
FROM Product JOIN
    PC ON PC.model = Product.model
WHERE PC.speed >= 450
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=10">10 задача</a></h2>

```sql
SELECT DISTINCT model, price
FROM Printer
WHERE price = (SELECT MAX(price) 
 FROM Printer
 )
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=11">11 задача</a></h2>

```sql
SELECT 
AVG(speed) 
AS Avg_speed 
FROM pc
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=12">12 задача</a></h2>

```sql
SELECT AVG(speed)
FROM Laptop
WHERE price > 1000
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=13">13 задача</a></h2>

```sql
SELECT AVG(speed)
FROM PC JOIN
Product ON Product.model = PC.model
WHERE Product.maker = 'A'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=14">14 задача</a></h2>

```sql
SELECT Ships.class, name, country
FROM Ships JOIN
Classes ON Classes.class = Ships.class
WHERE Classes.numGuns >= 10
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=15">15 задача</a></h2>

```sql
SELECT hd 
FROM pc 
GROUP BY (hd) 
HAVING COUNT(model) >= 2
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=16">16 задача</a></h2>

```sql
SELECT DISTINCT p1.model, p2.model, p1.speed, p1.ram
FROM pc p1, pc p2
WHERE p1.speed = p2.speed AND p1.ram = p2.ram AND p1.model > p2.model
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=17">17 задача</a></h2>

```sql
SELECT DISTINCT product.type, laptop.model, laptop.speed
FROM laptop, product
WHERE speed < (SELECT MIN(speed) FROM pc)
AND product.type ='Laptop'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=18">18 задача</a></h2>

```sql
SELECT DISTINCT A.maker, B.price
FROM Product A JOIN
 Printer B on A.model = B.model 
WHERE B.price = (SELECT MIN(price)
 FROM Printer 
 WHERE color = 'y') and B.color = 'y'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=19">19 задача</a></h2>

```sql
SELECT A.maker, AVG(B.screen)
FROM Product as A JOIN Laptop as B ON A.model = B.model
GROUP BY maker
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=20">20 задача</a></h2>

```sql
SELECT maker as Maker, COUNT(model) as Count_Model
FROM product
WHERE type='pc'
GROUP BY maker
HAVING COUNT(model)>=3
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=21">21 задача</a></h2>

```sql
SELECT Product.maker, MAX(PC.price)
FROM Product JOIN PC ON Product.model = PC.model
GROUP BY Product.maker
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=22">22 задача</a></h2>

```sql
SELECT speed, AVG(price)
FROM PC
WHERE speed > 600
GROUP BY speed
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=23">23 задача</a></h2>

```sql
SELECT DISTINCT maker
FROM product JOIN pc ON product.model=pc.model
WHERE speed>=750 AND maker IN
(SELECT maker
FROM product JOIN laptop ON product.model=laptop.model
WHERE speed>=750)
```
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=24">24 задача</a></h2>

```sql
SELECT model 
FROM (
 SELECT model, price FROM pc
 UNION
 SELECT model, price FROM laptop
 UNION
 SELECT model, price FROM printer
) table1
WHERE price = (
 SELECT MAX(price) 
FROM (
  SELECT price FROM pc
  UNION
  SELECT price FROM laptop
  UNION
  SELECT price FROM Printer
  ) table2
 )
 ```
 
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=25">25 задача</a></h2>

```sql
SELECT DISTINCT maker FROM product
WHERE model IN (
SELECT model FROM pc
WHERE ram = (SELECT MIN(ram)
  FROM pc
  )
AND speed = (
  SELECT MAX(speed)
  FROM pc
  WHERE ram = (
   SELECT MIN(ram)
   FROM pc
   )
  )
)
AND
maker IN (
SELECT maker
FROM product
WHERE type='printer'
)
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=26">26 задача</a></h2>

```sql
SELECT AVG(price) AS AVG_price FROM (SELECT model, price FROM PC
UNION ALL
SELECT model, price FROM Laptop) AS price
INNER JOIN product
ON price.model = product.model
WHERE maker = 'A'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=27">27 задача</a></h2>

```sql
SELECT p.maker, AVG(pc.hd) 
FROM product p JOIN pc pc ON p.model = pc.model 
WHERE pc.model IN (SELECT model FROM pc) AND maker IN (
SELECT maker FROM product WHERE type='printer') GROUP BY maker
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=28">28 задача</a></h2>

```sql
SELECT COUNT(maker) as Quantity FROM 
(
SELECT maker FROM product GROUP BY maker HAVING COUNT(*) = 1
) this_table
```
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=29">29 задача</a></h2>

```sql
SELECT income_o.point, income_o.[date], inc, out FROM income_o LEFT JOIN outcome_o ON outcome_o.point = income_o.point
AND outcome_o.[date]=income_o.[date]
UNION
SELECT outcome_o.point, outcome_o.[date], inc, out FROM income_o RIGHT JOIN outcome_o ON
outcome_o.point = income_o.point AND outcome_o.[date] = income_o.[date]
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=30">30 задача</a></h2>

```sql
SELECT point, [date], SUM(outs), SUM(incs) FROM
(SELECT point, [date], SUM(out) outs, null incs FROM outcome GROUP BY point, [date]
UNION
SELECT point, [date], null, SUM(inc) incs FROM income GROUP BY point, [date]) this_table GROUP BY point, [date]
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=31">31 задача</a></h2>

```sql
SELECT class, country
FROM classes
WHERE bore>=16
```
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=32">32 задача</a></h2>

```sql
SELECT country, cast(avg(bore*bore*bore/2) as numeric(38,2)) FROM
(SELECT country, name, bore FROM ships sh JOIN classes c ON sh.class=c.class
union
SELECT country, ship, bore FROM outcomes o JOIN classes c ON o.ship = c.class) t1
GROUP BY country
```
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=33">33 задача</a></h2>

```sql
SELECT ship
FROM Outcomes
WHERE battle = 'North Atlantic' AND result = 'sunk'
```
<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=34">34 задача</a></h2>

```sql
SELECT DISTINCT name 
FROM classes, ships 
WHERE launched >=1922 and displacement>35000 AND type='bb' AND
ships.class = classes.class
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=35">35 задача</a></h2>

```sql
SELECT model, type
FROM product
WHERE upper(model) NOT like '%[^A-Z]%'
OR model not like '%[^0-9]%'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=36">36 задача</a></h2>

```sql
SELECT DISTINCT name as Name FROM (
SELECT name FROM ships
UNION
SELECT ship FROM outcomes
) t1
WHERE name IN (SELECT class FROM classes)
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=37">37 задача</a></h2>

```sql
SELECT c.class FROM Classes c
LEFT JOIN (Select class, name FROM Ships
UNION
SELECT Classes.class as class, Outcomes.ship as name FROM Outcomes
JOIN Classes ON Outcomes.ship = Classes.class) as s On c.class = s.class
GROUP BY c.class
HAVING COUNT(s.name)=1
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=38">38 задача</a></h2>

```sql
SELECT DISTINCT country as COUNTRY
FROM classes
WHERE type='bb' AND country IN
(
SELECT country
FROM classes
WHERE type = 'bc'
)
```
