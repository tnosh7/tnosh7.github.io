---
title: JavaScript (1)
description: 기본 이론
date: 2024-06-11 12:00:00
categories: [Web, JavaScript]
tags: [web, javascript]     # TAG names should always be lowercase
---

# JavaScript (1)

## 1. 자바스크립트 생성방법

 1) 방법1

- 자바 스크립트의 문법은 `<script>` 태그 사이에서 작성한다.
- `<script>`태그는 명령어가 실행되는 순서에 따라서 `<head>` 또는 `<body>`부분에 위치한다.
- 과거에는 `<script type="text/javascript">`로 태그를 생성하지만 html5에서는 기술하지 않아도 된다.

**[중요]**

- 자바스크립트의 오류는 화면에 별도의 오류 메세지가 출력되지 않고 아무 반응이 없다
- 자바스크립트의 오류는 '웹 브라우저의 개발자도구 console'에서 확인할 수 있으므로, 	자바스크립트 코드 작성시에는 항상 console화면을 확인하면서 개발한다.
- 스크립트 코드가 웹 브라우저에 제대로 반영이 되지 않을 경우에는 웹브라우저에서 ctrl + f5 (캐쉬제거 새로고침)를 입력하여 변경된 결과를 확인한다.

```jsx
//1.document.write() : 데이터를 브라우저 화면에 출력하는 함수
document.write("복수의 데이터를 ", "출력할 수 ", "있습니다.")
//2.console.log() : 데이터를 '브라우저 콘솔'에 출력하는 함수
console.log("")
//3.alert() : 데이터를 '브라우저 안내창'으로 출력하는 함수
alert("")
```

 2) 방법2

- 외부에 스크립트 파일(.js)을 만들어 참조하여 자바스크립트를 사용할 수 있다.
- (.js)생성방법 : New > javaScript Source File
`<script src="경로">`형식으로 외부 스크립트 파일을 참조한다.
- 참조경로는 css파일 및 이미지 경로와 작성 방법이 같다.
- 공통 스크립트 및 무거운 파일을 주로 외부로 분류하여 사용한다.

```html
<head>
<script src="./example.js"></script>
</head>
```

## 2. 자바스크립트의 변수

- 자바스크립트에서의 변수는 데이터의 타입을 따로 명시하지 않고 `var` , `let`,  `const`으로 사용한다.
- 자바스크립트에서의 상수는 `const`를 사용한다.
- 변수의 역할, 명명규칙 , 활용 등은 다른 언어와 같다.
- 자바스크립트의 데이터 타입
    - 1) 숫자 (number)
    - 2) 문자열 (string)
    - 3) 불리언 (boolean)
    - 4) undefined
    - 5) 객체(object)
- 변수명 앞에 var(variable) , let 키워드를 붙여서 변수를 생성한다.
- 자바스크립트에서는 정수, 실수 모두 number 타입이다.
- 자바스크립트에서는 '' , "" 모두 string 타입이다.
- 초기화하지 않은 변수나 존재하지 않는 값의 데이터는 **undefined 타입**이다.
- 여러 값은 **Object 타입**이다.**`let 변수명 = { “변수명1” : 값1 , “변수명2” : 값2}`**

    ```jsx
	//typeof v1, v2 = number
	let v1= 1; 		
	let v2= 1.5;	
	//typeof v3, v4 = string
	let v3= '@';	
	let v4= "data"; 
	//typeof v5 = boolean
	let v5= true;
	//typeof v6 = undefined
	let v6;	
	//typeof v7 = object
	let v7 = {
		"pdCd" : "0x1234",
		"pdNm" : "스마트TV",
		"qty" : 1,
		"orderer" : "qwer1234",
		"isMobile" : true
	};
    ```

## 3. 데이터의 형변환

1. **String**(숫자) : 숫자 > 문자열 형변환 
    
    ```jsx
    let strVar1 = var1 + "";
    let strVar2 = String(var1);
    ```
    
2. **Number**(문자열) : 문자열 > 숫자 형변환
    
    ```jsx
    let nVar2 = Number(var2);
    ```
    
3. **parseInt**(실수) : 실수 > 정수  
4. 정수 / 정수 = 실수
    
    ```jsx
    let nVar3 = parseInt(var3);
    ```
    

---

## 4. 연산자

### 1) 산술 연산자

- 자바의 산술 연산자와의 차이점
    - 자바의 나눗셈 연산은 정수 but 자바스크립트의 나눗셈 연산은 **실수**
    - / 연산을 제외한 산술 연산자는 자바의 산술 연산자와 같다.

### 2) 복합 대입 연산자

- 자바의 복합 대입 연산자와 같다.

### 3) 증감 연산자

- 자바의 증감 연산자와 같다.

### 4) 비교 연산자

- [ 자바의 비교 연산자와의 차이점 ]
- 자바의 문자열 비교(==) 연산자의 결과 → 비교 불가 (.equals() 메서드 사용)
- 자바스크립트의 문자열 비교(==) 연산자의 결과  >  **비교 가능**
- "==" 연산을 제외한 비교 연산자는 자바의 비교 연산자와 같다.

### 5) 논리 연산자

- 자바의 논리 연산자와 같다.

### 6) 삼항 연산자

- 자바의 삼항 연산자와 같다.

### 7) 문자결합 연산자 +

1. 문자열 + 문자열 = 문자열
2. 문자열 + 숫자 = 문자열
3. 숫자 + 숫자 = 숫자

---

## 5. 출력

1. **confirm(”메시지”);**
    - **확인** 버튼을 클릭하면 **true**가 반환된다.
    - **취소** 버튼을 클릭하면 **false**가 반환된다.
    
    ```jsx
    let result = confirm("정말로 탈퇴하시겠습니까?");
    document.write(result);
    ```
    
2. **prompt("안내문자열" , "기본값");**
    - 기본 값은 생략 가능하다.
    - 기본 데이터 타입은 **문자열**이다.
    - 숫자 타입의 데이터는 추가적으로 숫자 형태로 형변환을 해주어야 한다.
    
    ```jsx
    let score = prompt("성적 입력");
    score = Number(score);
    console.log(60 <= score && score <= 100);
    ```
    

---

## 6. If문

- if문 default true
- 중첩 if문
- 자바와 같음

## 7. While문

- 자바와 같음