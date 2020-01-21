-- Q1

SELECT Name
FROM Salesperson
WHERE ID IN (
  SELECT DISTINCT salesperson_id
  FROM Orders
  WHERE cust_id = (
    SELECT ID
    FROM Customer
    WHERE Name = "Samsonic"
  )
);

-- Q2

SELECT Name
FROM Salesperson
WHERE ID IN (
  SELECT salesperson_id
  FROM Orders
  GROUP BY salesperson_id
  HAVING COUNT(*) >= 2
);

-- Q3

SELECT Name, Age
FROM Salesperson
WHERE Salary >= 100000;

-- Q4

SELECT MIN(order_date)
FROM Orders
WHERE cust_id = (
  SELECT ID
  FROM Customer
  WHERE Name = "Samony"
)
UNION ALL
SELECT MAX(order_date)
FROM Orders
WHERE cust_id = (
  SELECT ID
  FROM Customer
  WHERE Name = "Samony"
);

-- Q1

db.driver.find({"lastSeen":{ $gte:ISODate("2018-11-27"), $lt:ISODate("2018-12-27")}}).pretty();

-- Q2

db.driver.find({name:{$regex:'^(?i)j(?-i)ohnny '}});

-- Q3

db.driver.find({"vehicleData.make":"Toyota"}).pretty();
