---
layout: post
title: "GitHub 블로그에 Google Analytics 연결하기"
date:   2021-12-16 20:36:09 +0900
categories: jekyll update
comments: true
---

## 1. Google Analytics 계정 생성
- [Google Analytics](https://analytics.google.com/analytics/web/provision/?hl=ko&pli=1#/provision) 페이지에 접속

- `측정 시작`을 눌러 계정 생성<br/><br/><br/>



## 2. 데이터 스트림 설정
- 좌측 메뉴 하단에 `관리`를 눌러 `데이터 스트림` 창 선택

- `웹` 선택<br/><br/>
![](https://i.imgur.com/i0F2Jqg.png)

- `데이터 스트림` 설정
    1. https:// 선택 후 웹사이트 URL에 블로그 주소 입력

    2. 스트림 이름 설정
    
    3. 스트림 만들기<br/><br/>

    ![](https://i.imgur.com/qHXV6KN.png)<br/><br/><br/>



## 3. 측정ID 복사
- 웹 스트림 세부정보에서 측정ID 복사<br/><br/>
![](https://i.imgur.com/xm36lRe.jpg)<br/><br/><br/>



## 4. _config.yml 파일 수정
- _config.yml 파일 아래에 다음 코드 삽입
```
# Analytics
analytics:
  provider               : "google-gtag" 
                          # false (default), "google", "google-universal", "google-gtag", "custom"
  google:
    tracking_id          : "측정ID"
    anonymize_ip         : # true, false (default)
```

- tracking_id에 3에서 복사한 측정ID 붙여넣기<br/><br/>

![](https://i.imgur.com/y8vVSN6.jpg)<br/><br/><br/>

### ※ 내가 사용한 테마에는 *analytics.html*이 연결되어 있었지만 작동하지 않아 수정해주었음<br/><br/>

## 5. gtag.js 복사
- 3에서 측정ID를 복사했던 웹 스트림 세부정보에서 `태그하기에 대한 안내` -> `새로운 온페이지 태그 추가` -> 전체 사이트 태그 ... 클릭

- 아래 코드 복사<br/><br/>
![](https://i.imgur.com/gudx5Z7.jpg)<br/><br/><br/>



## 6. analytics.html 파일 수정
- _includes 폴더의 analytics.html 파일에 기존 코드 삭제하고 5에서 복사한 코드 입력<br/><br/>
![](https://i.imgur.com/8a49BM1.jpg)<br/><br/><br/>



## 7. 변경 사항 원격 저장소 반영
- git commit과 push 진행<br/><br/><br/>



## 8. 블로그에 방문하고 Google Analytics 확인
- 데이터 스트림에 입력한 블로그 방문

- Google Analytics 좌측 메뉴 상단에 `보고서` 선택하여 작동 확인<br/><br/>

![](https://i.imgur.com/WpCTuws.png)