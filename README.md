# 第二週的作業

DB：
訂飲料－可不可(Kebuke)

Table：
客戶(Customer)
訂單(Orders)
產品(Products)
廠商(Suppliers)


-- phpMyAdmin SQL Dump
-- version 4.9.3
-- https://www.phpmyadmin.net/
--
-- 主機： localhost:8889
-- 產生時間： 2020 年 08 月 07 日 09:32
-- 伺服器版本： 5.7.26
-- PHP 版本： 7.4.2

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET time_zone = "+00:00";

--
-- 資料庫： `Kebuke`
--

-- --------------------------------------------------------

--
-- 資料表結構 `customers`
--

CREATE TABLE `customers` (
  `CustomerID` int(2) NOT NULL,
  `CustomerName` varchar(40) NOT NULL DEFAULT '',
  `City` varchar(15) DEFAULT NULL,
  `Dist` varchar(15) DEFAULT NULL,
  `Rd` varchar(15) DEFAULT NULL,
  `Sec` int(3) DEFAULT NULL,
  `No` int(3) DEFAULT NULL,
  `Phone` varchar(24) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 傾印資料表的資料 `customers`
--

INSERT INTO `customers` (`CustomerID`, `CustomerName`, `City`, `Dist`, `Rd`, `Sec`, `No`, `Phone`) VALUES
(1, 'TigerCity', 'Taichung', 'Xitun', 'Henan', 3, 120, '(04)3606-8888'),
(2, 'Muji', 'Taichung', 'Xitun', 'TaiwanBlvd', 3, 301, '(04)2251-7151'),
(3, 'Carrefour', 'Taichung', 'Xitun', 'Qinghai', 2, 207, '0800-365005');

-- --------------------------------------------------------

--
-- 資料表結構 `orderdetails`
--

CREATE TABLE `orderdetails` (
  `OrderID` int(2) NOT NULL DEFAULT '0',
  `customerID` int(2) NOT NULL,
  `ProductID` int(2) NOT NULL DEFAULT '0',
  `Quantity` smallint(6) NOT NULL DEFAULT '0',
  `OrderDate` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 傾印資料表的資料 `orderdetails`
--

INSERT INTO `orderdetails` (`OrderID`, `customerID`, `ProductID`, `Quantity`, `OrderDate`) VALUES
(1, 1, 1, 5, '2020-08-08 12:00:00'),
(1, 1, 2, 5, '2020-08-08 12:00:00'),
(2, 2, 3, 10, '2020-08-08 13:00:00');
(3, 3, 4, 3, '2020-08-08 14:00:00'),
(3, 3, 5, 3, '2020-08-08 14:00:00'),


-- --------------------------------------------------------

--
-- 資料表結構 `products`
--

CREATE TABLE `products` (
  `ProductID` int(11) NOT NULL,
  `ProductName` varchar(40) NOT NULL DEFAULT '',
  `SupplierID` int(11) DEFAULT NULL,
  `UnitPrice` int(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

--
-- 傾印資料表的資料 `products`
--

INSERT INTO `products` (`ProductID`, `ProductName`, `SupplierID`, `UnitPrice`) VALUES
(1, 'SignatureBlackTea', 1, 30),
(2, 'BlackTea', 2, 30),
(3, 'GreenTea', 3, 30),
(4, 'MilkTea', 4, 50),
(5, 'PearlMilkTea', 5, 60);

--
-- 已傾印資料表的索引
--

--
-- 資料表索引 `customers`
--
ALTER TABLE `customers`
  ADD PRIMARY KEY (`CustomerID`);

--
-- 資料表索引 `products`
--
ALTER TABLE `products`
  ADD PRIMARY KEY (`ProductID`);

--
-- 在傾印的資料表使用自動遞增(AUTO_INCREMENT)
--

--
-- 使用資料表自動遞增(AUTO_INCREMENT) `customers`
--
ALTER TABLE `customers`
  MODIFY `CustomerID` int(2) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- 使用資料表自動遞增(AUTO_INCREMENT) `products`
--
ALTER TABLE `products`
  MODIFY `ProductID` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;
