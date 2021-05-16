```sql
### 데이터 정렬 
(order : 순서 / BY : ~에 의해 / BY 뒤에 기준 적기 )


[ 남자 회원 중 몸무게가 70kg 이상인 회원을 오름차순으로 정렬 ]
SELECT * FROM member
WHERE gender = 'm'
    AND weight >= 70
ORDER BY height ASC;



[ (여러 기준 정렬) 가장 최근에 가입한 사람부터 내림차순으로 정렬하고, 
같은 연도에 가입한 사람들은 이메일 기준으로 오름차순 정렬 ]
// ** 이름을 먼저 쓴 컬럼을 우선으로 해서 정렬이 차례대로 수행 됨 ** 

SELECT sign_up_day, email FROM member
ORDER BY YEAR(sign_up_day) DESC, email ASC;

---------------------------------------------------
### 정렬된 데이터에서 일부만 추려보기
// ** LIMIT : 현재 조회된 데이터 중에서 ~개만 조회하라는 의미 ** 


[ 최근에 가입한 회원 중 10명만 조회 ]
SELECT * FROM member
ORDER BY sign_up_day DESC 
LIMIT 10;



[ 최근에 가입한 회원 중 9, 10번째 가입한 회원 조회 ]
// 8번째 row부터 시작해서 총 2개의 row만 조회하라는 의미
// row는 0부터 시작함! 8은 9번쨰 row를 의미함 
SELECT * FROM member
ORDER BY sign_up_day DESC 
LIMIT 8, 2;



[ menu 테이블의 row들을 price 컬럼 기준으로 내림차순 정렬하고, 가격이 비싼 6~8위 데이터 조회 ]
SELECT * FROM menu 
ORDER BY price DESC
LIMIT 5, 3;



[ review 테이블에서 star(별점) 컬럼을 기준으로 오름차순 정렬하고, 
  같은 별점인 경우에는 registration_date(등록일자) 컬럼을 기준으로 내림차순 정렬하여 5개 데이터 조회.
  평가가 안 좋은 리뷰부터 최근 순으로 조회 ]
  
SELECT * FROM review
ORDER BY star ASC, registration_date DESC 
LIMIT 5;



---------------------------------------------------
### CAST
[ TEXT 타입의 컬럼인 registration_num에 있는 숫자값들을 기준으로 정렬할 때,
숫자가 작은 row들이 먼저 출력되게 하고 싶다면? ]

// CAST 함수 : 특정 데이터 타입의 컬럼에 저장된 값을 일시적으로 다른 데이터 타입으로 변경할 수 있게 해줌
// signed : 양과 음의 정수를 나타내는 데이터 타입 

SELECT * FROM sales 
ORDER BY CAST(registration_num AS signed); 

```
