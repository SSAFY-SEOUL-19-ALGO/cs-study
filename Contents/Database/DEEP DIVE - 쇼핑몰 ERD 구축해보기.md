# DEEP DIVE : 쇼핑몰 ERD 구축해보기

![Untitled](https://user-images.githubusercontent.com/47595515/211576205-31041ac8-5d38-452e-bb9e-0d4bfe2b2526.png)

## ERD 분석

![Untitled 1](https://user-images.githubusercontent.com/47595515/211576214-12dcc2d6-781e-462c-b3aa-bce5609f1c0d.png)

```sql
CREATE TABLE `customers` (
	`customerNumber` int(11) NOT NULL,
	`customerName` varchar(50) NOT NULL,
	`contactLastName` varchar(50) NOT NULL,
	`contactFirstName` varchar(50) NOT NULL,
	`phone` varchar(50) NOT NULL,
	`addressLine1` varchar(50) NOT NULL,
	`addressLine2` varchar(50) DEFAULT NULL,
	`city` varchar(50) NOT NULL,
	`state` varchar(50) DEFAULT NULL,
	`postalCode` varchar(15) DEFAULT NULL,
	`country` varchar(50) NOT NULL,
	`salesRepEmployeeNumber` int(11) DEFAULT NULL,
	`creditLimit` decimal(10,2) DEFAULT NULL,
	PRIMARY KEY (`customerNumber`),
	KEY `salesRepEmployeeNumber` (`salesRepEmployeeNumber`),
	CONSTRAINT `customers_ibfk_1` FOREIGN KEY
(`salesRepEmployeeNumber`) REFERENCES `employees`
(`employeeNumber`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

- decimal(10, 2) : 소수 부분을 포함한 실수의 총 자리수 10자리, 2개의 소수를 가지는 실수
- KEY : 인덱싱 할 키를 하나 더 생성

![Untitled 2](https://user-images.githubusercontent.com/47595515/211576224-eebbb755-f7ac-41ee-be05-d5cc39c620c0.png)

- 복합키(compound key) : orderNumber + productCode
    - 하나의 주문 안에 있는 상품코드들이 많을 경우 이를 구분하기 위해 2개의 키를 결합해야 유일성과 최서소성을 만족