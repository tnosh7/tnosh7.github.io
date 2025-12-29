---
title: github 블로그 만들기(2)
description: 테마 꾸미기
date: 2025-12-28 10:28:00
categories: [GithubBlog, Homepage]
tags: [githubblog, homepage]     # TAG names should always be lowercase
---

# github 블로그 만들기 (2) - 테마 꾸미기


# 테마를 설정하기 전에 앞서서,

## 1. ruby의 버전이 3.0 이상이어야 합니다.

[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/) 
* 터미널에 `ruby -v` 를 입력하여 루비 버전을 확인할 수 있습니다.

ruby 버전이 최소 3 버전 이상인지 체크해야 합니다.

MacOS(Intel)에는 기본적으로 ruby 2.6 버전이 설치되어 있지만, 이 상태에서 bundle을 통해 모듈을 설치할 경우 Chirpy에서 사용하는 모듈과 호환되지 않아 블로그 기능(다크모드, 검색, 이미지 표시, 모바일 환경 비정상 동작 등)이 정상적으로 동작하지 않습니다.

## 2. node.js가 설치 되어 있어야 합니다.

node.js 모듈을 설치하지 않으면 assets/js/dist/*.min.js Not Found 에러 발생과 함께 블로그 기능이 정상적으로 동작하지 않습니다.

---

# 테마 설정

1. branch를 master에서 main으로 변경하고 Branch protection rule도 기본값(체크 X)으로 설정한다.
2. 테마를 설치하기 위해 테마를 검색한 후 zip을 다운로드한다.
    - 참고: 테마 사이트
        
        [http://jekyllthemes.org/](http://jekyllthemes.org/) 
        
3. 다운로드한 테마를 압축을 풀어 닉네임.github.io 폴더에 넣는다. 
4. 테마 초기화를 진행합니다. 
    
    ```ruby
    gem install jekyll bundler
    cd user-name.github.io
    jekyll new ./
    ```
    
5. 테마 install
    - README 파일과 index.html 파일 모두 지워준다. 그리고 터미널에서 위의 폴더로 경로를 바꿔준다.
6. bundle 설치 
    
    ```jsx
    bundle install
    bundle exec jekyll serve --trace
    ```
    
- 오류 없이 성공적으로 진행되어 Server address: http://127.0.0.1:4000/ 가 뜨면 주소창에 http://127.0.0.1:4000/를 입력해보자. 기본 jekyll 페이지가 뜬다. 파란 글자로 Welcome to Jekyll!이 뜰 것.
1. push 
    
    ```jsx
    git add .
    git commit -m "commit!(커밋 메시지: 원하는 메시지로 설정할 수 있음)"
    git push
    ```
    

참고 사이트 

 [https://feb-dain.github.io/how-to-make-my-github-blog/](https://feb-dain.github.io/how-to-make-my-github-blog/)

[https://jjikin.com/posts/Jekyll-Chirpy-테마를-활용한-Github-블로그-만들기(2023-6월-기준)/](https://jjikin.com/posts/Jekyll-Chirpy-%ED%85%8C%EB%A7%88%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-Github-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0(2023-6%EC%9B%94-%EA%B8%B0%EC%A4%80)/)

---

<aside>
💡

## 에러 처리 과정 

</aside>

1. **tzinfo 에러** 
    - gem install tzinfo
    - gem install tzinfo-data
    
    위에 커맨드 창에 치고도 에러가 나는 경우 .gemfile을 열고 아래 코드를 쳐준다.
    
    ```jsx
    # Windows does not include zoneinfo files, so bundle the tzinfo-data gem
    gem 'tzinfo'
    gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
    ```
    
2. **js파일이 없다고 뜨는 에러** 
    
    `npm install && npm run build`
    
3. **--- layout: home # Index page -—**
    
    .js가 적용 안되는 오류.. 
    
    - page 세팅을 찾으러 가봄 .github-workflows-page-deploy.yml을 실행해봅니다.
    - 일단 처음부터 main branch로 생성한 것이 아니라 master branch로 생성을 하여 충돌이 난 것을 확인: branches에서 - master 를 삭제해줌
    - ruby -version을 내가 쓰고 있는 버전으로 맞춰줌
    - 왜 .js를 인식하지 못하지? 
    - .gitignore 실행해본다.
    - js를 무시하도록 설정된 코드를 주석 처리하여 js를 인식하도록 바꿈.
        
        ```
        //변경전
        # Misc
        _sass/dist
        assets/js/dist
        
        //변경후
        # Misc
        #_sass/dist
        #assets/js/dist
        ```
        
    
    참고 사이트 
    
    [https://ree31206.tistory.com/entry/github-pages-블로그-만들기-테마-적용하기Chirpy](https://ree31206.tistory.com/entry/github-pages-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0-%ED%85%8C%EB%A7%88-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0Chirpy)
    
    [https://velog.io/@hashnsalt/Github-Blog-만들기-2](https://velog.io/@hashnsalt/Github-Blog-%EB%A7%8C%EB%93%A4%EA%B8%B0-2)
