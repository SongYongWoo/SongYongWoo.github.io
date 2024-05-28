---
layout: single
title:  "[My SQL] 연산자"
categories : SQL
tag : [My SQL, operator]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

연산자

| 연산자 이름 | 종류              | 비고                                                     |
| :---------- | :---------------- | -------------------------------------------------------- |
| 사칙 연산자 | +, -, *, /        |                                                          |
| 비교 연산자 | =, <, >, <=, >=   |                                                          |
| 논리 연산자 | and, or, not      | and 와 or 이 같이 사용 될 경우, <br />and 조건 먼저 적용 |
| SQL 연산    | like, in, between |                                                          |

like  연산 : 특정 문자 찾기

```sql
select order_date, menu, user_id
from order_list ol 
where menu like '_m%';  -- 2번째 자리 문자가 m인 문자열만 출력

/*
_ : 문자 수 지정 
ex) __m__ : m 앞에 두글자, 뒤에 두글자만 존재해야 함
% : 몇개가 오든 상관 없음 
ex) m% : m이 맨 앞인 글자(글자 수 제한 없음)
*/
```



in 연산 

```sql
-- menu가 americano, moca, latte 중 하나인 경우 출력
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
where menu = 'americano' or menu = 'moca' or menu = 'latte';

||

select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
where menu in ('americano', 'moca', 'latte');
```



between 연산

```sql
-- 판매량이 1개 이상, 3개 이하인 경우 출력
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
where sales_qty >= 1 and sales_qty  <= 3;

||

select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
where sales_qty between 1 and 3;
-- 1과 3의 순서가 바뀌면 안됨. 바뀔 경우 출력 결과가 다름
```

