## 폼(form)태그
- 폼 태그는 텍스트 필드, 라디오 버튼, 체크 박스, 전송 버튼 등이 위치하게 함
- 사용자가 브라우저에 입력한 정보를 submit 버튼을 누르면 지정한 url로 정보를 전송

```html
<form method = "get" action = "confirm.php">
</form>
```

## 폼 태그 속성
- 폼은 사용자로부터 입력한 데이터를 처리해야 하기 때문에 기본적으로 통신방식을 설정하고, 처리하는 루틴을 읽어와야함
- **method** : 통신방법을지정, **get,post**방식 두가지가 있다.<br/>**get 방식**은 1KB이상의 데티러를 처리할때 사용, **post방식**은 1KB미만의 데이터를 처리할때 사용 
- **action** : 입력된 정보를 처리하는 프로그램의 경로를 지정

## 입력(input)태그
- 입력태그는 입력 양식 중 가장 기본적인 형태로 타입 속성값에 따라 여러가지 형태로 출력을 할수 있다 

## 입력 태그 속성
![image](https://user-images.githubusercontent.com/82345970/163739700-1df6f1e3-54e7-4f34-a080-dc9a4d017141.png)

### 텍스트(Text) 필드
- 임의의 문자를 입력 받을 때 사용하는 필드
```html
<input type="text" name="my_id">
```
- type 속성은 비단 텍스트 필드 뿐만 아니라 , 폼 태그 내에서는 필수적 속성
 
### 텍스트(Text) 필드 부가적 속성
![image](https://user-images.githubusercontent.com/82345970/163739784-51662907-4835-4386-8dff-d81a1591ea10.png)

### 텍스트(Text) 필드 예제
- maxlength="8" 8글자까지 작성할수 있게 설정
```html
<html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="get" action="">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요">
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="비밀번호을 입력하세요">
                
        </form>


    </body>

</html>
```
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/163740280-78698538-9e0d-4b33-8248-8bfb208150f2.png)

### 체크박스(checkbox)태그 만들기
- 출력결과에서 checked 작성 한거랑, 안 한거 비교해보기
```html
<html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="get" action="">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
                
        </form>


    </body>

</html>
```
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/163740731-ddae38ca-004d-4b36-b51b-5e686f88f082.png)

### radio태그 만들기
```html
<html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="get" action="">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
            <P>
            * 현재 당신의 PC를 포맷하시겠습니까?<p>
            <input type = "radio" name = "my_radio" value="yes" checked>예,포맷하겠습니다
            <input type = "radio" name = "my_radio" value="no">아니오  
        </form>


    </body>

</html>
 ```
 
### 출력결과
 ![image](https://user-images.githubusercontent.com/82345970/163742250-30bf5ead-569d-47ac-bb7b-d4e38d1f2b5e.png)

### submit태그 VS button태그
- 전송1은 submit get방식으로 처리하게 만들어준거고
- 전송2 button은 클릭에 대해서 처리 -> 버튼을 클릭하면 클릭에 대한 이벤트 핸들러
```html
<html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="get" action="">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
            <P>
            * 현재 당신의 PC를 포맷하시겠습니까?<p>
            <input type = "radio" name = "my_radio" value="yes" checked>예,포맷하겠습니다
            <input type = "radio" name = "my_radio" value="no">아니오
            <p>
            <!--
                 전송1은 submit get방식으로 처리하게 만들어준거고
                 전송2 button은 클릭에 대해서 처리 -> 버튼을 클릭하면 클릭에 대한 이벤트 핸들러
            -->    
            <input type = "submit" value = "전송1"><p>
            <input type = "button" value = "전송2">
        </form>


    </body>

</html>
```
### 출력결과 
![image](https://user-images.githubusercontent.com/82345970/163742989-15d57b9e-d577-4f65-bb91-7ffe6afa3130.png)
 
### 전송버튼 누를시 get방식으로 action예제
- <form method="get" action="../hello.html"> 전에 작성한 hello.html 불러옴
 
```html
<html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="get" action="../hello.html">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
            <P>
            * 현재 당신의 PC를 포맷하시겠습니까?<p>
            <input type = "radio" name = "my_radio" value="yes" checked>예,포맷하겠습니다
            <input type = "radio" name = "my_radio" value="no">아니오
            <p>
            
            <input type = "submit" value = "전송1"><p>
            
        </form>


    </body>

</html>
``` 
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/163743393-5efad2f4-740a-4eb7-aea2-7d8501501535.png)
 
 ### image태그
 ```html
 <html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="post" action="../hello.html">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
            <P>
            * 현재 당신의 PC를 포맷하시겠습니까?<p>
            <input type = "radio" name = "my_radio" value="yes" checked>예,포맷하겠습니다
            <input type = "radio" name = "my_radio" value="no">아니오
            <p>
            
            <input type = "submit" value = "전송1"><p>
            <input type = "image"  src = "../btn.png" width ="50" height="50">  
            
        </form>


    </body>

</html>
```
  
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/163744579-b74ea7a9-022f-4928-8c54-459b587c2d90.png)
  
### 선택박스(콤보박스)
- 예를들면 word에서 글꼴 선택 할때 나오는게, 콤보박스이다

```html
  <html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="post" action="../hello.html">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
            <P>
            * 현재 당신의 PC를 포맷하시겠습니까?<p>
            <input type = "radio" name = "my_radio" value="yes" checked>예,포맷하겠습니다
            <input type = "radio" name = "my_radio" value="no">아니오
            <p>
            
            <select value = "">
                <option value = ""당신의 세대는></option>
                <option value = "10"selected>10대</option>
                <option value = "20">20대</option>
                <option value = "30">30대</option>
                <option value = "40">40대</option>
                <option value = "50">50대</option>
            </select>    
            </p>    
            <input type = "submit" value = "전송1"><p>
            <input type = "image"  src = "../btn.png" width ="50" height="50">  
            
        </form>


    </body>

</html>
```

### 출력결과
- <option value = "10"selected>10대</option> 하면 10대 미리 선택되있음
   
![image](https://user-images.githubusercontent.com/82345970/163745238-4e94ed33-55a8-42c0-8b52-8e89cf5d160e.png)
   
### 파일업로드(file type)
```html
<html>
    <head>
        <meta content = "text/html"; charset="utf-8"/>
    </head>

    <body>
        <form method="post" action="../hello.html">
            아이디 : 
            <input type = "text" name = "my_id" size = "30" maxlength="8"
                value="이름을 입력하세요"><p>
            비밀번호 : 
            <input type = "password" name = "my_pwd" size = "30" maxlength="15"
                value="1111"><p>
            
            * 평소에 선호하는 언어의 종류를 고르시오 <p>
            <input type = "checkbox" name = "cb1" value= "C++" >C++
            <input type = "checkbox" name = "cb2" value= "자바" >자바
            <input type = "checkbox" name = "cb3" value= "아랍어" >아랍어
            <input type = "checkbox" name = "cb4" value= "자바스크립트" >자바스크립트
            <input type = "checkbox" name = "cb5" value= "파이썬" checked>파이썬        
            <P>
            * 현재 당신의 PC를 포맷하시겠습니까?<p>
            <input type = "radio" name = "my_radio" value="yes" checked>예,포맷하겠습니다
            <input type = "radio" name = "my_radio" value="no">아니오
            <p>
            
            <select value = "">
                <option value = ""당신의 세대는></option>
                <option value = "10"selected>10대</option>
                <option value = "20">20대</option>
                <option value = "30">30대</option>
                <option value = "40">40대</option>
                <option value = "50">50대</option>
            </select>    
            </p>    
            <input type = "submit" value = "전송1"><p>
            <input type = "image"  src = "../btn.png" width ="50" height="50">  
            <p>
            <input type = "file" name = "my_file">
                
        </form>


    </body>

</html>
``` 
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/163745456-8fdc8049-e066-48ea-9f6e-6edd292c8e95.png)
   

