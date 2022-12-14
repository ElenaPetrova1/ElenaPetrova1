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
SELECT DISTINCT model, ram, screen
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
SELECT DISTINCT model, speed, hd
FROM PC
WHERE price < 600 and cd = '12x' or price < 600 and cd = '24x'
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=6">6 задача</a></h2>

```sql
SELECT DISTINCT Product.maker, Laptop.speed
FROM Product 
JOIN Laptop 
ON Product.model = Laptop.model
WHERE hd >= 10
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=7">7 задача</a></h2>

```sql
SELECT model, price 
FROM PC 
WHERE model IN (SELECT model 
 FROM Product 
 WHERE maker = 'B' AND 
 type = 'PC'
 )
UNION
SELECT model, price 
FROM Laptop 
WHERE model IN (SELECT model 
 FROM Product 
 WHERE maker = 'B' AND 
 type = 'Laptop'
 )
UNION
SELECT model, price 
FROM Printer 
WHERE model IN (SELECT model 
 FROM Product 
 WHERE maker = 'B' AND 
 type = 'Printer'
)
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=8">8 задача</a></h2>

```sql
SELECT DISTINCT maker
FROM Product
WHERE type = 'PC'
EXCEPT
SELECT DISTINCT maker
FROM Product
WHERE type = 'Laptop'
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
SELECT AVG(speed)
FROM PC
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
FROM PC
GROUP BY hd
HAVING COUNT(hd) >= 2
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=16">16 задача</a></h2>

```sql
SELECT DISTINCT A.model AS model, B.model AS model, A.speed As speed, A.ram As ram 
FROM PC AS A, PC B 
WHERE A.speed = B.speed AND A.ram = B.ram AND A.model > B.model
```

<h2><a href="https://sql-ex.ru/learn_exercises.php?LN=17">17 задача</a></h2>

```sql
SELECT DISTINCT type, model, speed
FROM Laptop, (SELECT type FROM Product) AS ProductType
WHERE speed < ALL (SELECT speed FROM PC) and type = 'laptop'
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
SELECT DISTINCT Maker, COUNT(model)
FROM Product
WHERE type = 'PC'
GROUP BY Maker
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
