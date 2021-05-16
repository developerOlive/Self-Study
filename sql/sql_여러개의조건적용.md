```roomsql
### 여러 개의 조건 걸기 

[ 남자이며, 서울에 거주하는 25~29살 사이인 회원 ]
SELECT * FROM member
WHERE gender = 'm',
    AND address LIKE '서울%'
    AND age BETWEEN 25 and 29;
    
    
    
[ 봄(1~3) 또는 가을(7~9)에 가입한 회원 조회 (OR) ]
SELECT * FROM member
WHERE MONTH(sign_up_day) BETWEEN 3 AND 5
     OR MONTH(sign_up_day) BETWEEN 9 AND 11;



[ 남자이면서 키가 180 이상 이거나 여자이면서 170 이상인 회원 조회 ]
SELECT * FROM member
WHERE (gender = 'm' AND height >= 180)
    OR (gender = 'f' AND height >= 170);
    
    

[ 나이가 20대 이고, 가입한 달이 7월인 회원 ]
SELECT * FROM member
WHERE (age BETWEEN 20 AND 29) AND MONTH(sign_up_day) = 7;
   
    
--------------------------------------------------- 
### AND가 OR보다 우선순위가 더 높다!

[ 성별이 여자이거나(OR), 나이가 30세 미만이면서(AND) 키가 180인 이상인 회원 조회 ]
// 올바르게 실행되는 sql문 
SELECT * FROM member
WHERE (gender = 'f' OR age < 30) AND height > 180;   



// 올바르게 실행되지 않는 sql문
SELECT * FROM member
WHERE gender = 'f' OR age < 30 AND height < 180;


---------------------------------------------------
### Binary

[ 정확히 소문자 g만 들어간 데이터를 조회 (Binary를 안 붙이면 대문자 G가 들어간 데이터까지 조회 됨) ]
SELECT * FROM test
WHERE sentence
LIKE BINARY '%g%';

```
