```roomsql
### 함수

1. 연도, 월, 일 추출하기

[ 1992년에 태어난 회원들만 조회 ]
// YEAR 함수를 사용하면 날짜 값에서 연도만 뽑아낼 수 있음
SELECT * FROM member
WHERE YEAR(birthday) = '1992';



[ 6,7,8월에 가입한 회원들만 조회하기 ]
// MONTH 함수를 사용하면 날짜 값에서 월만 뽑아낼 수 있음

// IN 조건표현식을 활용하여 6,7,8월만 sorting
SELECT * FROM member
WHERE MONTH(sign_up_day) IN (6, 7, 8);



[ 각 달의 후반부(15~31일)에 가입했던 회원들만 조회 ]
// DAYOFMONTH 함수는 날짜 값에서 일만 뽑아낼 수 있음
// BETWEEN A AND B 구문을 이용해 15~31일 sorting

SELECT * FROM member
WHERE DAYOFMONTH(sign_up_day) 
BETWEEN 15 AND 31;


---------------------------------------------------
2. 날짜 간의 차이 구하기

[ 회원이 가입한 날짜가 2019년 1월 1일 기준으로 몇 일 이후인지 조회 ]
// DATEDIFF(날짜 a, 날짜b) : 날짜a - 날짜b = 차이 일 
SELECT email, sign_up_day,
DATEDIFF(sign_up_day, '2019-01-01')
FROM member;



[ 회원이 가입한 날짜가 오늘 날짜 기준으로 몇일 이후인지 조회 ]
SELECT email, sign_up_day, CURDATE(),
DATEDIFF(sign_up_day, CURDATE())
FROM member;



[ 회원이 몇 살 일 때 가입했는지 조회 ]
// 가입일 - 생일 / 365 = 회원이 몇 살 일 때 가입했는지 알 수 있음
SELECT email, sign_up_day,
DATEDIFF(sign_up_day, birthday) / 365
FROM member;


---------------------------------------------------
3. 날짜 더하기 빼기

[ 가입일(sign_up_day) 기준으로 300일 이후의 날짜 구하기 ]
SELECT email, sign_up_day,
DATE_ADD(sign_up_day, INTERVAL 300 DAY)
FROM member;



[ 가입일(sign_up_day) 기준 250일 이전의 날짜 구하기 ]
SELECT email, sign_up_day,
DATE_SUB(sign_up_day, INTERVAL 250 DAY)
FROM member;



4. UNIX Timestamp 값 
//  UNIX Timestamp는 특정 날짜의 특정 시간을 1970년 1월 1일을 기준으로, 총 몇 초가 지났는지로 나타낸 값

SELECT email, sign_up_day,
FROM_UNIXTIME(UNIX_TIMESTAMP(sign_up_day)) 
FROM member;

```
