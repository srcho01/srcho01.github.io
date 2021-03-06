# 프로젝트 Build 과정 
#### 소프트웨어학부 20213085 조서림
#### 블로그 주소 : <https://srcho01.github.io/><br/><br/></br>


## 1. GitHub 저장소 생성
나의 GitHub 페이지에 들어가서 블로그에 사용할 저장소를 생성한다.  
이 때, 저장소의 이름은 <사용자이름>.github.io의 형태이고, 공개 범위는 public이어야 한다.  
내가 자주 사용하는 아이디인 "srcho01"을 이용하여 저장소 srcho01.github.io을 생성했다.</br></br>


## 2. 로컬 저장소와 원격 저장소 연결
command 창에서 `cd` 명령어를 이용해 로컬 저장소를 생성하고 싶은 위치로 이동한다.  
그 후, `git clone <원격 저장소 URL>` 명령어로 원격 저장소를 나의 컴퓨터에 복제한다.</br></br>


## 3. 블로그 페이지 테스트
블로그가 정상적으로 동작하는지 확인하기 위해 html을 이용해 다음과 같은 index.html 파일을 작성한다.
```html
<!DOCTYPE html>
<html>
    <head>
        <title>GitHub Page Test</title>
    </head>
    <body>
        <h2>This is test page.</h2>
        <p>이 페이지가 잘 보인다면 성공!</p>
    </body>
</html>
```
index.html 파일을 commit하고 원격 저장소에 push한다.  
나의 블로그 <https://srcho01.github.io/>에 방문하여 테스트 페이지가 잘 뜨는지 확인한다.</br></br>


## 4. Jekyll 환경 준비
나는 프로젝트를 윈도우에서 진행하고 있기 때문에 먼저 [Ruby+Devkit](https://rubyinstaller.org/downloads/)을 설치한다.  
그 다음, command 창에서 `gem install jekyll bundler`를 이용해 지킬을 설치한다.  
설치가 완료됐다면 `jekyll -v` 명령어로 지킬이 잘 설치되었는지 확인한다.</br></br>


## 5. Jekyll 시작 
command 창에서 블로그 로컬 저장소로 이동하여 `jekyll new . --force` 명령어로 로컬 저장소에 지킬을 설치한다.  
`bundle exec jekyll serve` 명령어로 지킬 서버를 실행한다.  
인터넷 창에서 localhost:4000로 접속하여 기본 테마로 된 지킬 사이트가 생성되었음을 확인한다.</br></br>


## 6. 블로그와 지킬 사이트 연결
`git rm <파일명>` 명령어를 이용해 기존에 작성했던 index.html을 삭제하여 지킬 사이트가 내 블로그에서 정상적으로 실행되지 않는 문제를 방지한다.  
삭제한 index.html 파일과 새로 생성된 지킬 파일들을 commit하고 push한다.  
마찬가지로, 나의 블로그에 방문하여 지킬 사이트가 정상적으로 실행되는지 확인한다.</br></br>


## 7. 포스트 작성
블로그의 _posts 폴더 아래에 YYYY-MM-DD-<제목>.md 형태로 파일을 생성한다.  
포스트 제일 처음은 아래와 같은 형식으로 시작한다.  
```
---
layout: post
title: "포스트 제목"
date:   2021-12-16 13:05:12 +0900
categories: jekyll update
---
```
그 아래에 마크다운 형식을 이용해 포스트 내용을 작성한다.  
11월 12일 예시로 주어진 "MongoDB 정리" 포스트를 작성해 보았다.  
윈격 저장소에 commit, push 한 후 블로그에 접속해 작성한 포스트가 등록되었음을 확인한다.</br></br>


## 8. 새로운 테마 적용
* **테마 가져오기**  
먼저, 지킬 테마를 무료로 제공하는 [사이트](http://jekyllthemes.org/)에 방문하여 원하는 테마를 고른다.  
나는 아래의 *Lagom* 테마를 선택하였다.
![](https://i.imgur.com/wIOOGWk.png)
해당 테마의 GitHub 홈페이지에 방문해 깃허브 URL을 복사한다.  
우선 블로그 로컬 저장소와 다른 위치에 복사한 URL을 이용해 테마 저장소를 복제한다.  
블로그 로컬 저장소 _posts 폴더에는 내가 작성한 포스트가 존재하므로, _posts 폴더를 제외하고 테마 저장소의 파일들을 로컬 저장소에 추가하거나 덮어쓰기 한다.  

* **테마 반영하기**  
원격 저장소에 새로 생성된 파일들을 commit, push하여 반영한다.  
블로그에 접속해 테마가 정상적으로 적용되었는지 확인한다.

* **테마 정보 변경하기**  
git clone으로 복제해 적용한 테마에는 GitHub 주소나 이름 등 샘플 정보가 담겨 있으므로 나의 블로그에 맞게 변경한다.  
내가 변경한 파일과 정보들은 다음과 같다.  
  - _config.yml - 블로그 URL 변경
  - /_data/theme.yml - 이름 & 이메일 변경, GitHub 주소 변경, hacker_news와 twitter는 사용하지 않으므로 삭제, atom feed false로 변경
  - /_includes/footer.html - 블로그 포스트 목록 하단 문구 변경
  - /_includes/sidebar.html - 블로그 소개글 변경, 이메일 정보 추가
  - /_includes/social.html - GitHub만 사용하므로 "Follow Me" 대신 "GitHub"로 변경  

* **변경한 테마 모습**  
![](https://i.imgur.com/iMyBGhJ.png)</br></br>


## 9. 댓글 기능 추가
* **Disqus 세팅하기**  
[Disqus](https://disqus.com/) 홈페이지에 방문해 회원가입을 진행한다.  
platform은 Jekyll을 선택하고 Website URL에 나의 블로그 주소를 입력한다.  

* **_config.yml 파일 수정하기**  
_config.yml 파일 아래에 다음과 같은 코드를 추가한다.  
shortname에는 Disqus 가입 시 설정했던 username "srcho01"을 입력한다.  
    ```
    comment:
    provider:     "disqus"
    disqus:
        shortname:  "srcho01"
    ```

* **post.html 파일 수정하기**  
Disqus 사이트에서 우측 상단의 admin을 클릭한다.  
installing Disqus에서 Jekyll을 선택하고, 2번의 Universal Embed Code를 클릭하여 코드를 복사한다.  
_layouts 폴더에 post.html 파일을 열어 하단에 복사한 코드를 붙여넣는다.  
이 때, 코드의 위와 아래에 각각 `{% if page.comments %}`와 `{% endif %}`를 추가해 원하는 포스트에만 댓글 기능을 켤 수 있게 한다.  
`<h2>Comments</h2>`로 댓글창 위에 "Comments" 헤더를 달아준다.
    ```
    var disqus_config = function () {
        this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
        };
    ```
    위 코드의 주석을 해제하고, 그 위에 아래 코드를 삽입한다.
    ```
    let PAGE_URL = "{{site.url}}{{page.url}}"
    let PAGE_IDENTIFIER = "{{page.url}}"
    ```

* **포스트에서 댓글 활성화하기**  
포스트 머릿말에 `comments: true`를 추가하여 댓글을 활성화한다.

* **댓글 기능 추가 결과**  
![](https://i.imgur.com/kDp2PP8.png)</br></br>


## 10. Google Analytics 연결
블로그에서 Google Analytics를 연결한 과정을 포스트로 다루었다.  
[GitHub 블로그에 Google Analytics 연결](https://srcho01.github.io/jekyll/update/2021/12/16/Google-Analytics.html)</br></br>


## 11. favicon 추가
* **favicon 생성하기**  
파비콘으로 사용할 이미지를 찾는다.    
인터넷 탭 바가 흰색이 아닐 경우를 생각해 배경이 없는 PNG 파일을 선택했다.   
이미지를 파비콘으로 바꿔주는 [사이트](https://www.favicon-generator.org/)에 방문해 이미지를 파비콘으로 바꾼다.  
다운로드 후 압축을 해제하고 로컬 저장소의 assets 폴더 아래에 파비콘 폴더를 넣는다.  

* **default.html 파일 수정하기**  
_layouts 폴더에 default.html 파일을 열어 head 부분에 아래 코드를 삽입한다.  
    ```html
    <link rel="apple-touch-icon" sizes="57x57" href="/apple-icon-57x57.png">
    <link rel="apple-touch-icon" sizes="60x60" href="/apple-icon-60x60.png">
    <link rel="apple-touch-icon" sizes="72x72" href="/apple-icon-72x72.png">
    <link rel="apple-touch-icon" sizes="76x76" href="/apple-icon-76x76.png">
    <link rel="apple-touch-icon" sizes="114x114" href="/apple-icon-114x114.png">
    <link rel="apple-touch-icon" sizes="120x120" href="/apple-icon-120x120.png">
    <link rel="apple-touch-icon" sizes="144x144" href="/apple-icon-144x144.png">
    <link rel="apple-touch-icon" sizes="152x152" href="/apple-icon-152x152.png">
    <link rel="apple-touch-icon" sizes="180x180" href="/apple-icon-180x180.png">
    <link rel="icon" type="image/png" sizes="192x192"  href="/android-icon-192x192.png">
    <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
    <link rel="icon" type="image/png" sizes="96x96" href="/favicon-96x96.png">
    <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
    <link rel="manifest" href="/manifest.json">
    <meta name="msapplication-TileColor" content="#ffffff">
    <meta name="msapplication-TileImage" content="/ms-icon-144x144.png">
    <meta name="theme-color" content="#ffffff"> 
    ```
    이 때, `href` 뒤의 파일 경로 앞에 `/assets/favicon_io`를 추가해 나의 파일 경로와 맞게 작성한다.  

* **파비콘 설정 결과**  
![](https://i.imgur.com/8RUFZJU.png)