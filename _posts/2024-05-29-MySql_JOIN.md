---
layout: single
title:  "[My SQL] JOIN과 UNION"
categories : SQL
tag : [My SQL, JOIN, UNION]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가 
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

### JOIN

JOIN :    

- 여러 개의 테이블을 하나로 합칠 수 있음  
- N개의 테이블을 JOIN 하려면 N-1개의 JOIN이 필요함

```sql
select 테이블명.컬럼1, 테이블명.컬럼2 
from 테이블1 (left|right|inner) join 테이블 2
on (조인 조건)
```



![image-20240529123920204](/images/2024-05-29-JOIN/image-20240529123920204.png)

​                                                                                                                                                                                                      

### LEFT JOIN

조인 조건에 맞는 값과, 왼쪽 테이블 값을 출력. 오른쪽 값과 짝이 없는 경우 오른쪽 테이블의 값을 NULL로 표시

<img src="/images/2024-05-29-JOIN/image-20240529124155268.png" alt="image-20240529124155268" style="zoom:25%;" />

```sql
select A.C1, A.C2, B.C1, B.C2
from A left join B on A.C1 = B.C1;
```

![image-20240529124428854](/images/2024-05-29-JOIN/image-20240529124428854.png)



### RIGHT JOIN

조인 조건에 맞는 값과, 오른쪽 테이블 값을 출력. 왼쪽 값과 짝이 없는 경우 왼쪽 테이블의 값을 NULL로 표시

<img src="/images/2024-05-29-JOIN/image-20240529130702074.png" alt="image-20240529130702074" style="zoom:25%;" />

```sql
select A.C1, A.C2, B.C1, B.C2
from A right join B on A.C1 = B.C1;
```

![image-20240529130748823](/images/2024-05-29-JOIN/image-20240529130748823.png)



### INNER JOIN

조인 조건이 맞는 값만 출력

<img src="/images/2024-05-29-JOIN/image-20240529130915674.png" alt="image-20240529130915674" style="zoom:25%;" />

```sql
select A.C1, A.C2, B.C1, B.C2
from A inner join B on A.C1 = B.C1;
```

![image-20240529130934776](/images/2024-05-29-JOIN/image-20240529130934776.png)



### UNION과 UNION ALL

JOIN이 테이블을 가로로 합친다면, UNION (ALL)은 세로로 결합  
UNION : 데이터 중복을 없앰  
UNION ALL : 데이터 중복 허락  

주의점

1. 컬럼 수가 같아야 함.
2. 컬럼의 데이터 타입이 일치해야 함.

```sql
select c1, c2
from A
union
select c1, c2
from B;
```

![image-20240529131955615](/images/2024-05-29-JOIN/image-20240529131955615.png)

``` sql
select c1, c2
from A
union all
select c1, c2
from B;
```

![image-20240529132021189](/images/2024-05-29-JOIN/image-20240529132021189.png)





※ MySql은 FULL OUTER JOIN을 지원하지 않음.