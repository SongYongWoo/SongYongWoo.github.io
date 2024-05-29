---
layout: single
title:  "[My SQL] Database와 Table 생성"
categories : SQL
tag : [My SQL, Create]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가 
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

CREATE : 테이블, 데이터 베이스 등 생성

```sql
-- 데이터 베이스 생성
create database testdatabase;
```

![image-20240528213734351](/images/2024-05-28-CREATE/image-20240528213734351.png)



```sql
-- topic 테이블 생성
create table topic(
	-- 컬럼명 데이터 타입 제한조건
	id int(11) not null auto_increment,
    	-- not null : null 입력 불가
    	-- auto_increment : 자동으로 1씩 증가
	title varchar(100) not null, 
	description TEXT null,       -- null : null 허락
	created datetime not null,   -- datetime : 시간 포함
	author varchar(15) null,
	profile varchar(200) null,
	primary key(id));    -- 메인키. 중복 x null x
```

desc : 테이블의 구조 출력

```sql
desc topic;
```

![image-20240528214816535](/images/2024-05-28-CREATE/image-20240528214816535.png)