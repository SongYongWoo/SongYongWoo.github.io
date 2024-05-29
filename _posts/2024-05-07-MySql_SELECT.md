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
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

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





