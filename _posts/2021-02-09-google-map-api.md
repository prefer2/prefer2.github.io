---
title: "[TIL] google map api 사용하기"
date: 2021-02-09 13:26:28
tags: api js
categories: TIL
---

# 구글맵 API 사용하기

구글맵 api는 현재 첫 가입자에 한하여 12개월동안 무료(300달러 지급)로 사용이 가능하다.
(이후에도 개인 사용자가 사용할 정도는 무료로 사용이 가능한듯 하다. 혹시 몰라 [가격 측정표](https://cloud.google.com/maps-platform/pricing/?hl=ko&_ga=2.144176309.1250766310.1612838039-2145650309.1611557598))

사용하기 어려울 것 같지만 과정도 거의 없고 document도 정리가 잘 되어 있어 어렵지 않다

### 1. google cloud computing 가입

우선 아래 [홈페이지](https://cloud.google.com/gcp/?utm_source=google&utm_medium=cpc&utm_campaign=japac-KR-all-en-dr-bkws-all-all-trial-e-dr-1009882&utm_content=text-ad-none-none-DEV_c-CRE_496363162461-ADGP_Hybrid%20%7C%20BKWS%20-%20EXA%20%7C%20Txt%20~%20GCP%20~%20General%20_%20Core%20Brand-KWID_43700060620875343-kwd-26415313501-userloc_1009871&utm_term=KW_google%20cloud%20platform-ST_google%20cloud%20platform&gclid=Cj0KCQiA34OBBhCcARIsAG32uvNroAJ0849lRPsW2KZEo1ISMDY-t17bnTHa3EUtvnohI4_YU2k-xwcaAsGfEALw_wcB)에 접속하여 시작하기 또는 콘솔을 눌러 google cloud computing에 가입한다

[Google Cloud Computing, Hosting Services & APIs](https://cloud.google.com/gcp/?utm_source=google&utm_medium=cpc&utm_campaign=japac-KR-all-en-dr-bkws-all-all-trial-e-dr-1009882&utm_content=text-ad-none-none-DEV_c-CRE_496363162461-ADGP_Hybrid%20%7C%20BKWS%20-%20EXA%20%7C%20Txt%20~%20GCP%20~%20General%20_%20Core%20Brand-KWID_43700060620875343-kwd-26415313501-userloc_1009871&utm_term=KW_google%20cloud%20platform-ST_google%20cloud%20platform&gclid=Cj0KCQiA34OBBhCcARIsAG32uvNroAJ0849lRPsW2KZEo1ISMDY-t17bnTHa3EUtvnohI4_YU2k-xwcaAsGfEALw_wcB)

### 2. 프로젝트 선택 및 api 키 발급

<img width="1440" alt="스크린샷 2021-02-09 오후 12 32 18" src="https://user-images.githubusercontent.com/67692759/107314331-bdd07400-6ad7-11eb-88b9-035483a64d8d.png">

상단의 버튼을 누르면 어떤 프로젝트로 할 수 있는지 선택할 수 있다

기존의 My First Project를 사용해도 되고, 새 프로젝트를 생성하여 시작해도 된다
(프로젝트는 최대 9개까지 무료로 이용할 수 있다고 한다)

이후 메뉴에서 API 및 서비스 → 라이브러리를 선택한다

<img width="1076" alt="스크린샷 2021-02-09 오후 12 42 54" src="https://user-images.githubusercontent.com/67692759/107314368-cde85380-6ad7-11eb-8fbc-63fb82ec9ea4.png">

여기서 사용하고자 하는 서비스를 선택하면 된다
데이터베이스에서 위도 경도를 받아 표시하고자 하기 때문에 Maps JavaScript API를 선택하였다
사용 버튼을 누르고 API 및 서비스의 사용자 인증 정보에 들어가 새 API키를 받는다

### 3. 코드 가져오기

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Add Map</title>

    <link rel="stylesheet" type="text/css" href="./style.css" />
    <script src="./index.js"></script>
  </head>
  <body>
    <h3>My Google Maps Demo</h3>
    <!--The div element for the map -->
    <div id="map"></div>

    <!-- Async script executes immediately and must be after any DOM elements used in callback. -->
    <script
      src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&callback=initMap&libraries=&v=weekly"
      async
    ></script>
  </body>
</html>
```

html에 위 코드를 복사해 붙여넣어 YOUR_API_KEY부분에 이전에 받은 자신의 API 키를 붙여넣은다

이후 초기 설정, 마크 넣기 등은 JavaScript로 만들면 된다

### 4. 서울 시청을 중심으로 하고, 광화문에 마크가 있는 예시

```jsx
// Initialize and add the map
function initMap() {
// The location of Seoul city hall
	      const cityhall = { lat: 37.56642274261642, lng: 126.97799874175922 };
        // The map, centered at Seoul city hall
        const map = new google.maps.Map(document.getElementById("map"), {
          zoom: 12, //얼마나 zoom해서 보여줄 것인지
          center: cityhall,
        });
        // The marker, positioned at Seoul city hall
        const marker = new google.maps.Marker({
          position: cityhall,
          map: map,
        });
      }      
```

<img width="854" alt="스크린샷 2021-02-09 오후 12 57 42" src="https://user-images.githubusercontent.com/67692759/107314408-e5274100-6ad7-11eb-893c-488fff7db803.png">

참고로 위도와 경도는 구글맵에서 오른쪽 마우스 버튼을 누르면 나온다
다중 마커, 마커 이미지 바꾸기, 클러스터 등의 예시들은 공식 문서에 매우 잘 나와있다

[Maps JavaScript API  Google Developers](https://developers.google.com/maps/documentation/javascript/examples/marker-simple?hl=ko)
[이문서](https://developers.google.com/maps/documentation/javascript/adding-a-google-map?hl=ko)를 기반으로 작성되었습니다.
