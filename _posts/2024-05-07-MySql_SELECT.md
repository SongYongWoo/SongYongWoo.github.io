---
layout: single
title:  "[My SQL] 기본 조회 문법"
categories : SQL
tag : [My SQL, select]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

select : 결과창에 보여줄 값을 지정

``` sql
select 컬럼명 from 테이블명 ;
```

```sql
-- 사용할 데이터베이스 지정
use 데이터베이스;

select distinct 컬럼명  -- 중복되지 않은 속성값만 출력
	컬럼명 [as] 별칭 -- 별칭이 한글일 경우 "" 필요
from 테이블명 별칭 ;


/*
테이블의 별칭이 존재할 경우 컬럼명 앞에 "별칭."을 붙임
*/
select ol.menu from order_list ol;
```

![image-20240509224324806](/images/2024-05-07-SELECT/image-20240509224324806.png)

```sql
select distinct ol.menu from order_list ol;
```

![image-20240509224513105](/images/2024-05-07-SELECT/image-20240509224513105.png)





