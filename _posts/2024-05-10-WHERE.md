---
layout: single
title:  "[My SQL] where 절과 데이터 타입"
categories : SQL
tag : [My SQL, where, data type]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

where : 데이터 출력시  제한 조건 설정

```sql
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
where menu = 'americano';   -- menu 컬럼 중 americano만 출력
```

![image-20240510084547721](/images/2024-05-10-WHERE/image-20240510084547721.png)



데이터 타입

- Number : 숫자형, ' ' 필요 없음(있어도 상관 없으나 계산 시간이 오래 걸릴 수 있음)
  - Integger : 정수
  - Float : 실수
- String : 문자형, ' ' 필요
- DateTime : 날짜형, ' ' 필요
- Null : 데이터가 존재하지 않음

```sql
-- 정상적으로 Null 값 출력
select order_date, menu, user_id
from order_list ol 
where user_id is null; -- user_id 중 null 값을 출력

-- 잘못된 방법
select order_date, menu, user_id
from order_list ol 
where user_id = ''; -- user_id 중 빈 값을 출력

select order_date, menu, user_id
from order_list ol 
where user_id = null;  -- null은 등호로 표시 불가, 항상 false 값
```



