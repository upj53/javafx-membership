# JavaFX 멤버쉽 관리 애플리케이션 with Oracle Database
## 0.개발환경 설정

<details><summary>준비할 파일과 환경설정 모두보기</summary>
<pre>
▶▶▶▶▶준비하기◀◀◀◀◀
▷개발환경을 구성할 때 필요한 파일
1.eclipse-inst-jre-win64.exe
2.openjdk-15.0.2_windows-x64_bin.zip
3.openjfx-15.0.1_windows-x64_bin-sdk.zip
4.SceneBuilder-16.0.0.exe
5.OracleXE112_Win64.zip
6.sqldeveloper-21.2.0.187.1842-x64.zip
<br>
▶▶▶▶▶GUI 디자인 정보◀◀◀◀◀
▷컬러 코드
메인색 : #304dff
보조색 : #ccd3ff

▷GUI 폼 종류
1.공통
로그인 폼
2.사용자
회원가입 폼
회원정보 수정 폼
3.관리자
회원관리 폼
  
▷JavaFX FXML 변수
1.로그인 폼 JavaFX ID
체크박스 : adminCheckBox
사용자 아이디 : useridTextField
사용자 암호 : passwordPasswordField
로그인 버튼 : loginButton
회원가입 버튼 : registrationButton
취소 버튼 : cancelButton
창닫기 버튼 : closeButton

2-1.회원가입 폼 JavaFX ID
이름 : usernameTextField
아이디 : useridTextField
암호 : password1PasswordField
암호 확인 : password2PasswordField
학년 : hakTextField
반 : banTextField
번호 : bunTextField
회원가입 버튼 : submitButton
취소 버튼 : cancelButton
창닫기 : closeButton

2-2.회원정보 수정 폼 JavaFX ID
이름 : usernameTextField
아이디 : useridTextField
암호 : password1PasswordField
암호 확인 : password2PasswordField
학년 : hakTextField
반 : banTextField
번호 : bunTextField
회원가입 버튼 : modifyButton
취소 버튼 : resetButton
창닫기 : closeButton

3-1.회원관리 폼 JavaFX ID
이름 : usernameTextField
아이디 : useridTextField
암호 : password1PasswordField
암호 확인 : password2PasswordField
학년 : hakTextField
반 : banTextField
번호 : bunTextField
수정 버튼 : updateButton
삭제 버튼 : deleteButton
리스트 읽기 버튼 : readlistButton
창닫기 버튼 : closeButton
테이블 뷰 : membershipTableView
칼럼(이름) : userNameTableColumn
칼럼(아이디) : userIdTableColumn
칼럼(암호) : userPasswordTableColumn
칼럼(학년) : userHakTableColumn
칼럼(반) : userBanTableColumn
칼럼(번호) : userBunTableColumn

▶▶▶▶▶Java & FXML◀◀◀◀◀
▷Java FXML 파일과 Controller 연결관계 보기
0.Main.java
1.DBConnection.java
2.LoginController.java ↔ login.fxml
3.RegistrationController.java ↔ registration.fxml
4.ModificationController.java ↔ modification.fxml
5.MembershipController.java ↔ membership.fxml
</pre>
</details>
  
### 0-1.자바와 이클립스 설치와 HelloJavaFX
[![](http://img.youtube.com/vi/WwiBVttXo8k/0.jpg)](https://youtu.be/WwiBVttXo8k){:target="_blank"}

### 0-2.SceneBuilder 설치와 환경설정 그리고 HelloJavaFXML
[![](http://img.youtube.com/vi/udBUx-6wLto/0.jpg)](https://youtu.be/udBUx-6wLto){:target="_blank"}

### 0-3.Oracle 설치와 애플리케이션용 DB 생성 HelloOracleDB
[![](http://img.youtube.com/vi/cnf_qzN-UEQ/0.jpg)](https://youtu.be/cnf_qzN-UEQ){:target="_blank"}

## 1.GUI 구성 (SceneBuilder)

<details><summary>GUI 디자인 정보 보기</summary>
<pre>
▶컬러 코드
메인색 : #304dff
보조색 : #ccd3ff

▶GUI 폼
1.공통
로그인 폼
2.사용자
회원가입 폼
회원정보 수정 폼
3.관리자
회원관리 폼

▶JavaFX FXML 변수
1.로그인 폼 JavaFX ID
체크박스 : adminCheckBox
사용자 아이디 : useridTextField
사용자 암호 : passwordPasswordField
로그인 버튼 : loginButton
회원가입 버튼 : registrationButton
취소 버튼 : cancelButton
창닫기 버튼 : closeButton

2-1.회원가입 폼 JavaFX ID
이름 : usernameTextField
아이디 : useridTextField
암호 : password1PasswordField
암호 확인 : password2PasswordField
학년 : hakTextField
반 : banTextField
번호 : bunTextField
회원가입 버튼 : submitButton
취소 버튼 : cancelButton
창닫기 : closeButton

2-2.회원정보 수정 폼 JavaFX ID
이름 : usernameTextField
아이디 : useridTextField
암호 : password1PasswordField
암호 확인 : password2PasswordField
학년 : hakTextField
반 : banTextField
번호 : bunTextField
회원가입 버튼 : modifyButton
취소 버튼 : resetButton
창닫기 : closeButton

3-1.회원관리 폼 JavaFX ID
이름 : usernameTextField
아이디 : useridTextField
암호 : password1PasswordField
암호 확인 : password2PasswordField
학년 : hakTextField
반 : banTextField
번호 : bunTextField
수정 버튼 : updateButton
삭제 버튼 : deleteButton
리스트 읽기 버튼 : readlistButton
창닫기 버튼 : closeButton
테이블 뷰 : membershipTableView
칼럼(이름) : userNameTableColumn
칼럼(아이디) : userIdTableColumn
칼럼(암호) : userPasswordTableColumn
칼럼(학년) : userHakTableColumn
칼럼(반) : userBanTableColumn
칼럼(번호) : userBunTableColumn
</pre>
</details>
  
<details><summary>Java FXML 파일과 Controller 연결관계 보기</summary>
<pre>
0.Main.java
1.DBConnection.java
2.LoginController.java ↔ login.fxml
3.RegistrationController.java ↔ registration.fxml
4.ModificationController.java ↔ modification.fxml
5.MembershipController.java ↔ membership.fxml

MVC 디자인 패턴을 사용하는 Java 프로그래밍 기법
</pre>
</details>

### 1-1.SceneBuilder 로그인 폼
[![](http://img.youtube.com/vi/G5ypEZekaJc/0.jpg)](https://youtu.be/G5ypEZekaJc){:target="_blank"}

### 1-2.SceneBuilder 회원가입 폼과 회원정보 수정 폼
[![](http://img.youtube.com/vi/D63n9r8WRWw/0.jpg)](https://youtu.be/D63n9r8WRWw){:target="_blank"}

### 1-3.SceneBuilder 회원관리 폼
[![](http://img.youtube.com/vi/Ephh5lQ-l8k/0.jpg)](https://youtu.be/Ephh5lQ-l8k){:target="_blank"}

## 2.FXML/데이터베이스 연결
### 2-1.FXML이벤트 생성과 연결
[![](http://img.youtube.com/vi/fwtjP5wqqtw/0.jpg)](https://youtu.be/fwtjP5wqqtw){:target="_blank"}

### 2-2.Oracle 데이터베이스 연결과 테이블 생성
[![](http://img.youtube.com/vi/2m0badpnQr0/0.jpg)](https://youtu.be/2m0badpnQr0){:target="_blank"}

## 3.로그인 모듈
### 3-1.LoginController 로그인 체크 함수(관리자와 멤버)
[![](http://img.youtube.com/vi/_VifYYLQ1NA/0.jpg)](https://youtu.be/_VifYYLQ1NA){:target="_blank"}

### 3-2.로그인모듈, 관리자와 사용자 로그인 로직 만들기
[![](http://img.youtube.com/vi/ttv_vIXm2e0/0.jpg)](https://youtu.be/ttv_vIXm2e0){:target="_blank"}

### 3-3.로그인 모듈, 로그인 계정에 따른 새창 열기
[![](http://img.youtube.com/vi/cFTJUtAdWTI/0.jpg)](https://youtu.be/cFTJUtAdWTI){:target="_blank"}

## 4.회원가입 모듈
### 4-1.회원가입 모듈, FXML버튼의 이벤트 정의하기
[![](http://img.youtube.com/vi/9bO-R6Q4vnQ/0.jpg)](https://youtu.be/9bO-R6Q4vnQ){:target="_blank"}

### 4-2.회원가입 모듈, 입력폼 체크와 SQL INSERT 실행
[![](http://img.youtube.com/vi/oLgLypQyUCM/0.jpg)](https://youtu.be/oLgLypQyUCM){:target="_blank"}

## 5.회원정보 수정 모듈
### 5-1.회원정보수정, 초기화 인터페이스 구현과 Initializable
[![](http://img.youtube.com/vi/rZoM9W2p4s0/0.jpg)](https://youtu.be/rZoM9W2p4s0){:target="_blank"}

### 5-2.회원정보수정, 회원정보 입력값 검사와 SQL UPDATE 실행
[![](http://img.youtube.com/vi/sF33oK0_JXI/0.jpg)](https://youtu.be/sF33oK0_JXI){:target="_blank"}

## 6.관리자 회원관리 모듈
### 6-1.관리자 회원관리 테이블뷰 자료구조와 제네릭
[![](http://img.youtube.com/vi/NIO9EktdmmU/0.jpg)](https://youtu.be/NIO9EktdmmU){:target="_blank"}

### 6-2.관리자 회원관리 테이블뷰 SQL SELECT
[![](http://img.youtube.com/vi/3xL6E_gvKAg/0.jpg)](https://youtu.be/3xL6E_gvKAg){:target="_blank"}

### 6-3.관리자 회원관리 테이블뷰 item 자료읽어서 보여주기
[![](http://img.youtube.com/vi/qGfFpGnqPZA/0.jpg)](https://youtu.be/qGfFpGnqPZA){:target="_blank"}

### 6-4.관리자 회원관리 테이블뷰 SQL DELETE
[![](http://img.youtube.com/vi/ZGBzUqWVQQw/0.jpg)](https://youtu.be/ZGBzUqWVQQw){:target="_blank"}

### 6-5.관리자 회원관리 테이블뷰 SQL UPDATE
[![](http://img.youtube.com/vi/KLlBkHpqGk8/0.jpg)](https://youtu.be/KLlBkHpqGk8){:target="_blank"}
