---
title: github 블로그 만들기(1)
description: 홈페이지 생성
date: 2024-06-06 12:00:00
categories: [GithubBlog, Homepage]
tags: [githubblog, homepage]     # TAG names should always be lowercase
---


# github 블로그 만들기 (1) - 홈페이지 생성


## 왜 깃헙 블로그?

**Github Blog의 장점**은,

1. **유저가 모든 것을 직접 수행해야 한다는 것**. 
    
    웹 개발자라면 경험하는 웹 개발 과정과 유사하다. 다만, 이클립스 같은 에디터를 통해서가 아니라 명령 프롬프트를 통해서 한다고 생각하면 쉽게 접근할 수 있을 것 같다.    
    
2. **리눅스 기본 명령어를 경험할 수 있다**. 
cmd에서 git 경로에 가는 것도 `cd git` 이런 식으로 해야 한다. 파일 올려 내려 등 그동안의 과정을 진행하면서 리눅스 명령어에 익숙해지는 경험을 하였다. 
3. **Github Blog를 통해 개발자로서의 프로페셔널함을 표현할 수 있다**. 
쉽고 간편한 블로그가 많은데도 불구하고 github를 선택한 것은 세계적인 포럼에서 나의 개발 실력을 증명하는데도 좋고 개인 포트폴리오에서도 도움이 될 거라는 생각 때문이다. 또한 git을 많이 쓰기 때문에 여러 사이트로 옮겨 다니지 않아도 된다는 편리함도 있다. 

---

## github blog 만들기 전에 기본 세팅하기

1. 당연하게도 **github**에 가입되어 있어야 합니다. 
    - [https://github.com/](https://github.com/)
        
        사이트 상단에 **Sign Up**을 눌러서 가입해주세요. 
        
        ![image](https://tnosh7.github.io/assets/img/github.png)
        
    
2. 로컬 컴퓨터에 **git**이 **설치**되어 있어야 합니다.

      git 주소에 들어가서 자신의 컴퓨터에 맞는 버전을 다운로드 해주세요.

- [https://git-scm.com/downloads](https://git-scm.com/downloads)
    
    ![image](https://tnosh7.github.io/assets/img/git.png)
    
    

---

## Github Blog 만들기 (1) - 홈페이지 생성

1. **Repository 생성**을 합니다.  
    
    ![image](https://tnosh7.github.io/assets/img/CreateRepository.png)
    
    ![image](https://tnosh7.github.io/assets/img/CreateRepository2.png)
    

<aside>
💡 Repository name 에 **닉네임.github.io** 를 붙여준다.

</aside>

여기서 입력한 Repository name은 추후에 블로그 주소가 됩니다.

<aside>
💡 **Public**으로 체크해서 생성한다.

</aside>

<aside>
💡 **Add a README file**을 추가한다.

</aside>

<aside>
💡 **Create repository** 클릭한다.

</aside>

1. 생성된 Repository 닉네임.github.io **주소를 복사**합니다. 

1. 로컬 컴퓨터에서 **git** 이라는 폴더가 있는 지 확인해봅시다. 
    
    *기본 경로: C:\Users\로컬컴퓨터 사용자명\git
    
2. Window + R 누른 후에 cmd 입력                           **OR**
    
    윈도우 검색에서 cmd 검색 후 명령 프롬프트 클릭 
    
3.  **C:\Users\사용자명 >** 이 보입니다. 
    
    내가 C드라이브\사용자\로컬컴퓨터 사용자명 > 폴더 안에 들어왔다고 생각하시면 됩니다. 
    
    3번 과정을 통해서 git의 위치를 확인하고 왔습니다. 이제 git의 폴더로 진입해봅시다.
    
    ```jsx
    **cd git**
    ```
    
    **C:\Users\로컬컴퓨터 사용자명\git >** 이 보이면 git폴더로 진입했다는 뜻입니다. 
    
4. **Git Clone** 하기 
아까 복사한 repository 주소를 붙여서 원격 저장소와 로컬 컴퓨터를 연결하여 관리하기 편리한 환경을 조성할 겁니다.  
    
    ```jsx
    **git clone 아까 복사한 주소 붙여넣기** 
    ```
    
    예를 들면 저는 git clone https://github.com/tnosh7/tnosh7.github.io.git 를 입력하면 되겠죠? 
    
    제대로 실행되면,
    
    ```jsx
    Cloning into ‘닉네임.github.io’ …
    중간생략…
    resolving deltas : 100% (1/1), done.
    ```
    
    이라는 과정이 나올 겁니다. 
    
     * ‘git’은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다.’ 라는 오류가 나시는 분들은  **[git 설치](https://git-scm.com/downloads)**하고 오세요. 
    
5. 로컬 git에 **index.html 파일 생성**하기 
    
    인터넷 홈페이지에 주소를 입력하면 뜨는 기본 파일을 생성해 볼 것입니다. 
    
    ```jsx
    **cd 닉네임.github.io
    echo "Hello World" > index.html**
    ```
    
    아까 Clone한 repository로 진입합니다. 
    
    “Hello World”라는 text가 적힌 html문서 index.html을 생성합니다. 
    로컬컴퓨터의 git폴더에서 index.html문서가 생성됐는지 확인합니다. 
    
6. **원격 저장소에 올리기** 
    
    지금까지 로컬저장소에 생성했으니 이제 원격저장소에 저장할 차례입니다. 
    
    **무엇을 저장 → 중간 저장 → 원격저장소 저장** 의 단계를 거쳐 저장됩니다.  
    
    ```jsx
    **git add *
    git commit -m "메시지"
    git push -u origin main**
    ```
    
    - **git add ***  : git 폴더에 변경 사항을 모두(* = -A = All) staging에 저장한다는 의미의 명령어입니다.
    - **git commit -m “메시지**” : 앞서 변경 사항을 확정하겠다는 의미입니다. “메시지”는 쉽게 한줄요약 같은 거라 생각하면 됩니다. 나중을 생각해서 확인하기 쉽게 꼭 적어줍시다.
    - **git push** : 원격 저장소에 업로드합니다.
    - **-u origin main** : 메인 브랜치를 origin으로 올리겠다는 의미입니다.
    
7. **https://닉네임.github.io/  주소창에 입력**해봅니다. 
    
    ![image](https://tnosh7.github.io/assets/img/HelloWorld.png)
    
    참고) github repository에서 index.html과 deployments도 확인해보세요.  
    

---
## 오류 확인     
 - git clone 또는 commit 과정에서 아래와 같이 오류가 나시는 분들이 있을 수 있습니다.
    
    ```jsx
    * Please tell me who you are.
    Run
    git config --global user.email "[you@example.com](mailto:you@example.com)"
    git config --global [user.name](http://user.name/) "Your Name"
    
    to set your account's default identity.
    Omit --global to set the identity only in this repository.
    ```
    
    자격 증명이 확인이 안돼서 생기는 오류로 친절하게 보여준 메시지처럼 아래와 같이 코드를 입력해주면 됩니다. 
    
    ```jsx
    **git config user.email** "가입이메일"
    **git config user.name** "유저이름"
    ```
    
    다음에 오류가 난 과정부터 다시 진행해주시면 됩니다. 
    
 - **Sign in with your browser**
    
    push를 하는 과정에 github에 로그인하라는 화면이 뜨시는 분들이 있을 수 있습니다. 처음 push하는 과정에서 자연스럽게 발생하는 과정이니 새로 뜬 창에서 로그인하셔서 인증을 진행하시면 됩니다. 

---

이상으로 첫 Github Blog 과정을 마쳤습니다.

다음은 **홈페이지 꾸미기**를 해보도록 하겠습니다.