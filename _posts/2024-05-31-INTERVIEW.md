---
layout: single
title:  "[SQL Server] Face book, Apple, Uber 면접 문제 변형"
categories : SQL
tag : [SQL Server, INTERVIEW]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

### Face book

 각 월별로 얼마나 사람들이 친구 수락을 하였는 지 확인하는 쿼리 작성

Activity Table

| Activity_ID | User1_ID | User2_ID | Activity_type | Activity_date |
| ----------- | -------- | -------- | ------------- | ------------- |
| 1           | 1001     | 1101     | 'Accept'      | '2021-1-07'   |
| 2           | 1002     | 1102     | 'Accept'      | '2021-1-15'   |
| 3           | 1003     | 1103     | 'Accept'      | '2021-1-15'   |
| ...         | ...      | ...      | ...           | ...           |

``` sql
-- 방법 1
SELECT 
FORMAT(Activity_date, 'yyyyMM') as Activity_Month, 
Count(Activity_type) as Accept_Num
FROM Activity
WHERE Activity_type = 'Accept'
GROUP BY FORMAT(Activity_date, 'yyyyMM');

-- 방법 2
SELECT MONTH(Activity_date) as Acticity_month,  -- MONTH : 달 추출
sum(case when Activity_type = 'Accept' then 1 else 0 end) as Accept_num
FROM Activity
Group by month(Activity_date);
```

![image-20240531095326774](/images/2024-05-31-INTERVIEW/image-20240531095326774.png)



### Apple

일 별로 같은 날 앱과 웹에 둘 다 접속한 유저의 수를  파악

Web_log Table

| web_log_id | User_ID | date         |
| ---------- | ------- | ------------ |
| 1          | 2001    | '2021-01-01' |
| 2          | 2002    | '2021-01-02' |
| 3          | 2003    | '2021-01-03' |
| ...        | ...     | ...          |

App_log Table

| app_log_id | User_ID | date         |
| ---------- | ------- | ------------ |
| 1          | 2001    | '2021-01-01' |
| 2          | 2002    | '2021-01-02' |
| 3          | 2003    | '2021-01-03' |
| ...        | ...     | ...          |

```sql
select 
W.date as Usage_Date, 
count(DISTINCT W.User_ID) as User_Number
from Web_log as W join App_log as A    
	on W.User_ID = A.User_ID        -- 유저 id가 동일하며
	AND W.date = A.date             -- 동일한 날짜가 있는 경우로 JOIN
group by W.date;
```

![image-20240531100058896](/images/2024-05-31-INTERVIEW/image-20240531100058896.png)



### Uber

유저가  프리미엄 서비스와 베이직 서비스를 선택하여 사용 가능. Orders Table은 여러 개의 user_name을 중복되게 가질 수 있음.   
이 중 프리미엄 서비스를 사용하지만, 베이직 서비스를 사용하지 않은 고객의 리스트 출력

| Order_ID | User_Name | Service_type | Service_date |
| -------- | --------- | ------------ | ------------ |
| 1        | 'Mike'    | 'Basic'      | '2021-1-07'  |
| 2        | 'John'    | 'Basic'      | '2021-1-15'  |
| 3        | 'Dave'    | 'Basic'...   | '2021-1-15'  |
| ...      | ...       | ...          | ...          |

```sql
-- Premium 서비스를 받은 사람 중에 Basic 서비스 받은 사람 빼기
select User_name
from Orders
where Service_type = 'Premium'
except             
select User_name
from Orders
where Service_type = 'Basic';
```

![image-20240531101258337](/images/2024-05-31-INTERVIEW/image-20240531101258337.png)