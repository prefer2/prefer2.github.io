---
title: "[TIL] 서버 개발 환경 셋팅"
date: 2021-06-18 17:36:28
tags: django aws
categories: TIL
---
## Virtualenv

여러개의 파이썬 프로젝트가 하나의 컴퓨터에서 충동을 일으키지 않고 존재할 수 있도록 도와준다

각 프로그램별론 독립적인 가상의 환경을 만들어냄으로써 패키지/라이브러리간 version issue 또는 dependency issue를 차단하고, 프로젝트에서 사용하는 패키지/라이브러리를 관리하거나 정리하기 수월하게 도와준다.

### 설치

`pip install virtualenv`

### 가상환경

`virtualenv 가상환경명`

### 활성화

`가상환경명/Scripts/activate`

### 비활성화

`deactivate`

## WSGI

`python manage.py runserver`는 단지 테스트 해보기 위한(개발을 위한) 명령어

실제 서비스에서는 사용하지 않음

→ 실제로는 nginx같은 웹 서버를 사용해야 함

 WSGI(Web Server Gateway Interface)는 웹서버와 웹 프레임워크 사이에 통신을 담당하는 인터페이스. 즉 웹서버와 Django 사이에 통신을 담당한다.

## web server

웹서버란 HTTP를 통해 웹 브라우저에서 요청하는 HTML 문서나 오브젝트(이미지 파일 등)을 전송해주는 서비스 프로그램. 클라이언트로부터 요청(request)을 받아 뒤에 웹 어플리케이션으로 전달하고, 그에 대한 응답(respone)을 다시 클라이언트로 전달한다. 대표적으로 Nginx, apache가 있다.

- 인증
- 정적 콘텐츠 관리
- HTTPS 지원
- 콘텐츠 압축
- 가상 호스팅
- 대용량 파일 지원
- 대역폭 스로틀링

## 참조

[서버개발자가 되는법 [1] - 서버 개발환경 셋팅, AWS EC2만들고 Django 프로젝트 실행해보기](https://cholol.tistory.com/484?category=966420)

[서버개발자가 되는법 [2] - 서버 개발환경 셋팅, Nginx와 uWSGI 설치해서 연결하기 + docker로 mysql 띄우기](https://cholol.tistory.com/485?category=966420)
