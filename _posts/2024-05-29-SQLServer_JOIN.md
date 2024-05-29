---
layout: single
title:  "[SQL Server] JOIN, INTERSECT, EXCEPT"
categories : SQL
tag : [SQL Server, JOIN, INTERSECT, EXCEPT]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

![image-20240529210814473](/images/2024-05-29-SQLServer_JOIN/image-20240529210814473.png)

### INNER JOIN

조인조건에 맞는 결과 값만 출력

<img src="/images/2024-05-29-JOIN/image-20240529130915674.png" alt="image-20240529130915674" style="zoom:25%;" />

```sql
SELECT 테이블1.컬럼명, 테이블2.컬럼명
FROM 테이블1 JOIN 테이블2
ON 조인조건

SELECT A.c1, A.c2, B.c1, B.c2
FROM A join B
on A.c1 = B.c1;
```

![image-20240529210850464](/images/2024-05-29-SQLServer_JOIN/image-20240529210850464.png)

### FULL OUTER JOIN

조인조건에 맞는 값 뿐만 아니라 양쪽 테이블의 나머지 값들도 모두 출력

<img src="/images/2024-05-29-SQLServer_JOIN/image-20240529204948497.png" alt="image-20240529204948497" style="zoom:25%;" />

```sql
SELECT 테이블1.컬럼명, 테이블2.컬럼명
FROM 테이블1 full JOIN 테이블2
ON 조인조건

SELECT A.c1, A.c2, B.c1, B.c2
FROM A full join B
on A.c1 = B.c1;
```

![image-20240529210947991](/images/2024-05-29-SQLServer_JOIN/image-20240529210947991.png)



### INTERSECT

세로로 결합. 중복되는 값만 출력

<img src="/images/2024-05-29-SQLServer_JOIN/image-20240529213836081.png" alt="image-20240529213836081" style="zoom:25%;" />

```sql
select c1, c2
from A
intersect
select c1, c2
from B;
```

![image-20240529213733252](/images/2024-05-29-SQLServer_JOIN/image-20240529213733252.png)



### EXCEPT

세로로 결합. 위 테이블 내용 중 아래 테이블에 없는 내용만 출력

<img src="/images/2024-05-29-SQLServer_JOIN/image-20240529214100975.png" alt="image-20240529214100975" style="zoom:25%;" />

```sql
select c1, c2
from A
except
select c1, c2
from B;
```

![image-20240529214138449](/images/2024-05-29-SQLServer_JOIN/image-20240529214138449.png)



```sql
-- 다른 데이터베이스에선 except 대신 minus 사용
select c1, c2
from A
minus
select c1, c2
from B;
```



※ 세로 결합 시, 컬럼의 데이터 타입과 갯수가 일치해야 함.
