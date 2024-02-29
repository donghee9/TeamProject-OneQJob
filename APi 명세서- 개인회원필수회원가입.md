

### branch Individual Member necessary Sign up
### RequestBody
```
POST /user/signup/general HTTP/1.1
Content-Type:application/json

{
	"userName":"(이름)", 
	"phoneNumber":"(휴대폰 번호)",
	"imgFileName":"(프로필 사진 이름)", null
	"imgUrl":"(프로필 사진 url)", null
	"dateOfBirth":"(생년월일)",
	"userId":"(아이디)",
	"userPw":"(비밀번호)"
	"sessionId":"sjdkfnjsk;fdnskj",
	"address":{ 
		"roadAddress":"(도로명주소)", *
		"sido":"(시도)", * 
		"sigungu":"(시군구)", *
		"bname":"(동)"    null
		"bname1":"(읍면리)", null
		"detailAddress":"(상세주소)" null
	}
}
```
### ReponseBody
```
201 Created HTTP/1.1
Content-Type: application/json

{
	"success":true
	"message":"user create successfully"
	"data":{
		"userName":"(유저네임)"
		"userId":"(유저아이디)"}
}
```
### 설계시 고려사항

유효성 검사항목

1.  필드값 다 들어왔는지 확인 
2.  user id 중복 확인 (이미 이 아이디를 가진 사용자가 있는 확인)
3.  유효성 확인
    - *userId  8~16자리 , 영문 대문자 소문자 특수문자 외에 다른 text는 안됨.*
    - *userPw  8자리 ~16자리 , 영문 대문자 소문자 특수문자 다 포함해서 비번을 만들어야 함.*

< 백 > → 내부 에러 코드도 보내주기 bname , bname1 둘중 하나 null 확인하기

###  성공 케이스

case1) 모든사항 전부 기입 and 아이디 중복여부 & 아이디, 비번 유효성통과

case2) 필수사항 기입 and 아이디 중복여부 & 아이디, 비번 유효성통과


###  실패 케이스

case1) 필수사항 누락

case2) 유저아이디 중복

case3) 유저아이디 유효성 통과 불가

case) 비밀번호 유효성 통과 불가
