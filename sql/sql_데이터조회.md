# SQL

- SELECT : 테이블의 데이터를 조회할 때 사용
- ' * '(Asterisk) : 테이블의 모든 컬럼값을 조회한다는 의미
- FROM : 조회하고 싶은 테이블명 기재

```sql
[ 30대만 제외하여 조회 ]
SELECT * FROM member 
WHERE age NOT BETWEEN 30 AND 39;



[ 2019년 1월 1일 이후 가입자만 조회 ]
SELECT * FROM member 
WHERE sign_up_day > '2019-01-01';



[ 2018년도 가입자 조회 ]
SELECT * FROM member 
WHERE sign_up_day BETWEEN '2018-01-01' AND '2018-12-31';



[ 주소가 서울이라는 단어로 시작하고 임의의 길이를 가진 문자열 조회 ]
SELECT * FROM member
WHERE address LIKE '서울%';



[ 고양시 라는 단어가 포함된 모든 문자열 조회 ]
SELECT * FROM member
WHERE address LIKE '%고양시%';



[ 남자(m)가 아닌 회원들만 조회 ]
SELECT * FROM member
WHERE gender != 'm';

SELECT * FROM member
WHERE gender <> 'm';



[ 회원 중 나이가 20살 또는 30살인 회원만 조회 ]
SELECT * FROM member 
WHERE age IN (20, 30);



[ 메일 주소가 c로 시작하고, 그 뒤에 여섯 글자가 있는 회원 조회 ]
SELECT * FROM member 
WHERE email LIKE 'c______@%';



[ 한 글자의 성으로 시작되고, 성 바로 다음에 '현'자가 들어있고, '현'자 뒤에는 ㅇㅁ의의 길이의 문자열이 있는 회원 조회 ]
SELECT * FROM member
WHERE name LIKE '_현%'; 



[나이가 20 또는 30 또는 40인 회원 조회 ]
SELECT * FROM member
WHERE age IN (20, 30, 40);
```
