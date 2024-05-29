---
layout: single
title:  "[My SQL] Group by와 집계함수를 활용한 간단한 데이터 분석"
categories : SQL
tag : [My SQL, Group by, '집계함수']
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}






```sql
-- 일간/시간당 매출
select order_date "일자",
		substr(order_time, 1, 2)"시각",
		sum(sales_qty * price) "매출"
from order_list
group by order_date, substr(order_time, 1, 2)
order by 1, 2, 3 desc;
```



![image-20240528172823188](/images/2024-05-28-GROUP_BY_TEST/image-20240528172823188.png)

```sql
-- 메뉴 별 판매 횟수 조회
select order_date "일자",
		menu "메뉴", 
		count(sales_qty) "판매 횟수"
from order_list
group by order_date, menu
order by 1, 2;
```

![image-20240528172851007](/images/2024-05-28-GROUP_BY_TEST/image-20240528172851007.png)

```sql
-- 고객별 마지막 방문일, 총 주문 횟수, 총 주문 금액
select user_id, 
	max(order_date) "마지막 방문일",
	sum(sales_qty) "총 주문 횟수",
	sum(sales_qty * price) "총 주문 금액"
from order_list
where user_id is not null and 
	user_id  <> ''
group by user_id;
```

![image-20240528172910032](/images/2024-05-28-GROUP_BY_TEST/image-20240528172910032.png)