## SQL

## SQL의 종류

### 데이터 정의어(DDL)

> 스키마, 도메인, 테이블, 뷰, 인덱스 등 데이터의 구조를 정의하거나 제거
> 
> CREATE, ALTER, DROP이 있다.

#### 형식:

-   ##### CREATE
    
    > ```null
    > CREATE TABLE [테이블명] ( 속성 );
    > ```
    
-   #### DROP
    
    > ```null
    > DROP TABLE [테이블명];
    > ```
    
-   #### ALTER
    
    > 스키마, 도메인, 테이블, 뷰, 인덱스 등 데이터의 구조를 정의하거나 제거
    > 
    > ```null
    > ALTER TABLE [테이블명] ADD [속성이름] [타입]; ALTER TABLE [테이블명] DROP [속성이름] [CASCADE]; ALTER TABLE [테이블명] RENAME COLUMN [속성이름] to [변경이름]; ALTER TABLE [테이블명] MODIFY [속성이름] [타입];
    > ```
    
-   #### FOREIGN KEY
    
    > \[참조할 테이블명\]\_\[참조할 컬럼명\]으로 네이밍하고 아래와 같이 참조해준다.
    > 
    > ```null
    > FOREIGN KEY (컬럼명) REFERENCES [참조할 테이블명] (참조할 컬럼명)
    > ```
    
    ##### SQL에서 주석은 #으로 사용한다.
    

### 데이터 조작어(DML)

> 실질적으로 데이터를 조회 삽입, 삭제, 수정할 때 사용하는 SQL
> 
> SELECT DELETE UPDATE INSERT가 있다.

#### 형식:

-   ##### INSERT(삽입)
    
    > ```null
    > INSERT INTO [테이블명] ([컬럼 값(자동삽입 값 제외하고 명시)]) VALUES ([명시한 컬럼과 맞는 순서의 속성]);
    > ```
    
-   ##### UPDATE(수정)
    
    > ```null
    > UPDATE [테이블명] SET [컬럼명]=[바꿀 값] WHERE [조건식]
    > ```
    
-   ##### DELETE(삭제)
    
    > ```null
    > DELETE FROM [테이블명] WHERE [조건식]
    > ```
    
-   ##### SELECT(검색)
    
    ORDER BY \[컬럼명\] ASC(오름차순) or DESC(내림차순), 다음정렬;
    
    > ```null
    > SELECT [컬럼명 or *] from [테이블명] WHERE [조건식]
    > ```
    
-   ##### GROUP BY
    
    > 컬럼을 유형별로 그룹화 할 때 사용하며 WHERE이 아닌, HAVING으로 조건을 건다
    > 
    > GROUP BY를 사용하려면 반드시 SELECT 문에 집계함수만 있거나, GROPU BY 뒤에 명시해줘서 그룹화 할 수 있어야 한다.(추가)
    > 
    > ```null
    > GROUP BY [컬럼명] HAVING [조건식]
    > ```
    

-   #### 기타 옵션
    
    -   IS NULL, IS NOT NULL
    -   LIKE, NOT LIKE
    -   LIMIT

#### SQL Injection

> 사용자가 id, pwd에 다음과 같이 입력한다면?  
> id: ewqewq1' = '1' OR '1' = '1'##  
> pwd: ewqewq

![](https://velog.velcdn.com/images/kangking/post/b160cd06-bf1c-4bcb-ae3d-7150a7496824/image.png)

-   ##### \## 뒷부분이 주석처리 되어 조건을 정상적으로 끝까찌 참조하지 않아 로그인에 성공해버린다.
    
    ##### JPA등을 사용하는 이유가 이런 동작들이 발생하지 않도록 자동화 해주기 때문이다.
    
    ##### 일반적으로 프론트 단에서도 주석이나 SQL에 변형을 줄 수 있는 특수문자는 입력을 제한 하는 등의 노력을 같이 한다.
    

### JOIN

> 실제 실무에서는 하나의 테이블에서만 값을 가져오지 않고 여러 테이블의 값을 조회한다.
> 
> 테이블을 먼저 합치고, WHERE절로 원하는 값을 가져온다.

-   #### Inner JOIN(교집합)
    
    > 지정한 값과 같은 값만 join
    
    ![](https://velog.velcdn.com/images/kangking/post/1f008832-e80d-49f4-9d8d-82a1cfded510/image.png)
    
    ![](https://velog.velcdn.com/images/kangking/post/c9b0e4fa-5b8d-4350-a64b-810bc450b201/image.png)
    

-   #### Left JOIN(많이 씀)
    
    > 왼쪽에 기준이 되는 테이블을 출력하고 오른쪽에 지정한 값과 일치하는 테이블 값을 출력한다.
    
    ![](https://velog.velcdn.com/images/kangking/post/1470c878-e998-4e26-a9a5-3ced067d3284/image.png)
    
    ![](https://velog.velcdn.com/images/kangking/post/3de72fce-ba61-44fb-8299-2d32b1b44f1b/image.png)
    

-   #### Right JOIN
    
    > 오른쪽에 기준이 되는 테이블을 출력하고 왼쪽에 지정한 값과 일치하는 테이블 값을 출력한다.
    
    ![](https://velog.velcdn.com/images/kangking/post/18f0db96-ae66-435d-921f-46c3319a04d9/image.png)
    
    ![](https://velog.velcdn.com/images/kangking/post/7b1282e8-9eb7-41d3-ba2b-491c4b3ea442/image.png)