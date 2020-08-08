# 第二週的作業

DB：訂飲料－可不可(kebuke)

Table：客戶(customers)、訂單明細(orderdetails)、訂單(orders)、產品(products)

1.請先透過「bak.sql」建立資料庫、資料表及其資料。
※其中「OrderID」希望是用月份+日期+流水號編碼，例如080801，所以另外設了zerofill，讓首碼可以為零。
  

2.請透過以下指令瀏覽各資料表的資料:
SELECT * FROM `customers`;
SELECT * FROM `orderdetails`;
SELECT * FROM `orders`;
SELECT * FROM `products`;
   
3.請透過以下指令列出給備餐人員的清單:
SELECT od.OrderID as '訂單編號', ProductName as '品名', Quantity as '數量'
FROM orderdetails AS od
JOIN products AS p 
ON od.ProductID = p.ProductID;

4.請透過以下指令列出給外送人員的清單(含訂單編號、客戶名稱、地址、電話、客戶要求的送達時間與應跟客戶收的總金額):
SELECT o.OrderID as '訂單編號', CustomerName as '客戶名稱', City, Dist, Rd, Sec, No, Phone, Time as '送達時間', SUM(Quantity * UnitPrice) AS '總金額'
FROM orders AS o
JOIN customers AS c 
ON o.CustomerID= c.CustomerID
JOIN orderdetails AS od 
ON o.OrderID = od.OrderID
JOIN products AS p 
ON od.ProductID = p.ProductID
GROUP BY o.OrderID;
