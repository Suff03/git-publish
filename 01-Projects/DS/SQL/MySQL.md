1994년 스웨덴에서 개발 시작, 무료, 오픈 소스, 관계형 데이터베이스 시스템

WEB 개발자들의 많은 사랑을 받음 (동반 성장)

----
스프레드시트vs데이터베이스

공통점 : 데이터를 표의 형태로 표현

스프레드시트 : 클릭을 통해 데이터 조작

데이터베이스 : SQL을 통해(컴퓨터 언어) 데이터 조작

데이터를 분석, 공유할 수 있음 (WEB이 대표적)

---
MySQL 구성요소
표(table) - 데이터를 기록하는 최종적인 곳
스키마(데이터베이스) - 서로 연관된 table을 그룹핑한 일종의 폴더
데이터베이스 서버 - 스키마 저장

---
스키마 만들기
외우려고 하지 말고 중요한 건 검색을 통해 찾아내는 능력..

```MySQL
CREATE DATABASE tutorials;
```

스키마 삭제
```MySQL
DROP DATABASE tutorials;
```

데이터베이스 리스트
```MySQL
SHOW DATABASES;
```

USE (데이터베이스 사용)
```MySQL
USE tutorials;
```

![[Pivot-Table-Data-Source-Structure.webp]]

---
SQL?
Structured Query Language
Structured 정리정돈(구조화)
Query 데이터베이스에 질의
Language 공통의 약속에 따라..

SQL - 쉬움, 중요함

---
테이블 생성
```MySQL
CREATE TABLE topic(
	id INT(11) NOT NULL AUTO_INCREMENT,
	title VARCHAR(100) NOT NULL,
	description TEXT NULL,
	created DATETIME NOT NULL,
	author VARCHAR(15) NULL,
	profile VARCHAR(200) NULL,
	PRIMARY KEY(id)
);
```

NOT NULL // 값이 없는 것 허용 X
AUTO_INCREMENT 1씩 증가
VARCHAR(size) 가변 길이 허용 CHAR형
PRIMARY KEY(c1) 메인 키 - 성능, 중복X

---
CRUD

Create
Read
Update
Delete

---
Create

DESC (Name) // 테이블 구조 출력

```MySQL
INSERT INTO topic (title, description, created, author, profile) VALUES('MySQL', 'MySQL is...', NOW(), 'egoing', 'developer')
```

---
Read

```MySQL
SELECT * FROM topic
SELECT id, tltile, created ,author FROM topic WHERE author='egoing' ORDER BY id DESC LIMIT 2; 
```

// WHERE 조건
ORDER BY 순서 (DESC) 내림차.
LIMIT (n) n개까지 출력

---
Update


```MySQL
UPDATE topic SET description='Oracle is ...', title='Oracle' WHERE id=2;
```

WHERE문 필수


---
Delete
```MySQL
DELETE FROM topic WHERE id = 5;
```

WHERE문 필수


---
데이터베이스
본질 : CRUD
혁신 : 관계형 데이터베이스

---
왜 관계형 데이터베이스가 필요한가?

중복된 데이터 문제 해결 용이 (여러 테이블 만들기)
trade-off 직관적으로 데이터 보기 어려운 단점

해결)
저장할 때는 별도로 테이블 보관
	보여줄 때는 합쳐서