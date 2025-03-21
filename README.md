# spring-practice-scheduler
<br>

# 기본 스케줄러  
## 스케줄러 API
|기능|Method|URL|request|response|상태조회|
|---|---|---|---|---|---|
|일정 생성|`POST`|`/api/schedule/add`|`요청 body`<br> json <br> {<br> "schedule": "할일", <br> "name": "작성자명", <br> "password": "비밀번호", <br> "creation_date": "작성일시"<br>}|`등록정보`<br> json <br> {<br> "id": "고유값", <br> "schedule": "할일", <br> "name": "작성자명", <br> "creation_date": "작성일시", <br> "modification_date": "수정일시"<br>}|`200 : 정상 등록`|
|전체 일정 조회|`GET`|`/api/schedule`|`요청 param`<br> modification_date, name|`다건 응답 정보`<br> json <br> [{<br> "id": "고유값", <br> "schedule": "할일", <br> "name": "작성자명", <br> "creation_date": "작성일시", <br> "modification_date": "수정일시"<br>}, ...]|`200 : 정상 조회`|
|선택 일정 조회|`GET`|`/api/schedule/{scheduleID}`|`요청 param`|`단건 응답 정보` <br> json <br> {<br> "id": "고유값", <br> "schedule": "할일", <br> "name": "작성자명", <br> "creation_date": "작성일시", <br> "modification_date": "수정일시"<br>}|`200 : 정상 조회`|
|선택한 일정 수정|`PUT`|`/api/schedule/{scheduleID}`|`요청 body`<br> json <br> {<br> "schedule": "할일", <br> "name": "작성자명", <br> "password": "비밀번호"<br>}|`수정 정보`<br> json <br> {<br> "id": "고유값", <br> "schedule": "할일", <br> "name": "작성자명", <br> "creation_date": "작성일시", <br> "modification_date": "수정일시"<br>}|`200 : 정상 수정`|
|선택한 일정 삭제|`DELETE`|`/api/schedule/{scheduleID}`|`요청 param`<br> { "password": "비밀번호" }|-|`200 : 정상 삭제`|

## 스케줄러 ERD
![화면 캡처 2025-03-21 205020](https://github.com/user-attachments/assets/e6fbb81d-6af6-43df-bba0-ae877f633ae5)

## 스케줄러 SQL
```
CREATE TABLE schedule_post (
	id INT(10) NOT NULL PRIMARY KEY,
	schedule VARCHAR(255) NOT NULL,
	name VARCHAR(10) NOT NULL,
	password VARCHAR(30) NOT NULL,
	creation_date DATETIME NOT NULL,
	modification_date DATETIME NULL
);
```
