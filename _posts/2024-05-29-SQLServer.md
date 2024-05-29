---
layout: single
title:  "[SQL Server] 기본, TOP"
categories : SQL
tag : [SQL Server, TOP]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

### 기본 사용법

```sql
-- 사용할 데이터베이스 언급
use [데이터베이스];

-- 기본 조회식
select 컬럼 from 테이블
where 조건
order by 컬럼 [asc|desc];
```



### TOP

TOP : 상위 일정 데이터만 출력

```sql
-- 컬럼 중 해당 숫자 상위 컬럼을 출력
select TOP 숫자
	컬럼 
from 테이블
where 조건
order by 컬럼 [asc|desc];

-- Customer 테이블에서 나이 순으로 어린 나이 2명 정보 출력
SELECT TOP 2 * 
FROM Customer
ORDER BY age;
```

![image-20240529195547337](/images/2024-05-29-SQLServer/image-20240529195547337.png)

```sql
-- 오라클 문법
select 컬럼 
from 테이블
where 조건
order by 컬럼 [asc|desc]
limit 숫자;
```

