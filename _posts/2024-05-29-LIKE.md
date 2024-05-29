---
layout: single
title:  "[My SQL] LIKE"
categories : SQL
tag : [My SQL, LIKE]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---

### LIKE

LIKE : 특정 문자를 가진 속성값들을 찾기 위해 사용 

```sql
where 컬럼명 LIKE '표현식'
```

| 표현식                            | 설명                                   |
| --------------------------------- | -------------------------------------- |
| name like 'A%'                    | A로 시작하는 값                        |
| name like '%A%'                   | A가 포함된 값                          |
| name like '%A'                    | A로 끝나는 값                          |
| name like '_A%'                   | 두 번째 글자가 A인 값                  |
| name like '\_&nbsp;\_A\_&nbsp;\_' | A가 3번째에 위치하며, 총 길이가 5인 값 |

\_  : 자릿수 표현(한 자리)

% : 자릿수 상관 없음(0 이상)



```sql
-- c가 포함된 메뉴 츌력
select distinct menu from order_list ol 
where menu like '%c%';   
```

![image-20240529191144313](/images/2024-05-29-LIKE/image-20240529191144313.png)

```sql
-- 두 번째 글자가 a인 메뉴 출력
select distinct menu from order_list ol 
where menu like '_a%';
```

![image-20240529191323549](/images/2024-05-29-LIKE/image-20240529191323549.png)