---
title: "[CSS] checkbox 디자인 변경"
date: 2021-02-04 16:26:28
tags: css html
categories: css
---

## CSS checkbox 디자인

css에 기본으로 주어진 checkbox는 단순하고 수정이 어렵다. 

checkbox를 안보이게 하고, 그 위에 label로 덮어쓰는 형식으로 checkbox를 디자인 할 수 있다.

css로 위치 조정을 해서 checkbox가 선택지 뒤로 가게 하였고, checkbox 선택 시 색상을 변경하였다.

(줄이 있는 칸에 넣고 check칸을 둥글게 하기 위해 bootstrap의 list-group, rounded사용)

html

```html
<div class="vote">
	 <ul class="list-group">
          <li class="list-group-item vote-title">투표하기</li>
          <li class="list-group-item"><input type="checkbox" id="voteIndex1"/>
            <label for="voteIndex1" class="rounded"><span class="vote-num">01</span><span class="vote-thing">vote1</span></label>
          </li>
        
          <li class="list-group-item"><input type="checkbox" id="voteIndex2"/>
            <label for="voteIndex2" class="rounded"><span class="vote-num">02</span><span class="vote-thing">vote2</span></label>
          </li>
        
          <li class="list-group-item"><input type="checkbox" id="voteIndex3"/>
            <label for="voteIndex3" class="rounded"><span class="vote-num">03</span><span class="vote-thing">vote3</span></label>
          </li>
    </ul>
 </div>
```

css

```css
.vote-title{font-weight: 700;}
.vote ul {list-style: none;}
.vote ul li input[type="checkbox"] {display: none;}
.vote ul li input[type="checkbox"] + label { width:17px; height: 17px; border:#666464 solid 1px; cursor: pointer; float: right;}
.vote ul li input[type="checkbox"]:checked + label {content: "\2714"; background:url(../src/image/check_white.png)#3F3FEA center/12px 12px; float: right}
.vote-thing{position: absolute; left: 30px;}
.vote-num{position: absolute; left: 5px; color: #bcbcbc;}
```

결과

<img width="365" alt="스크린샷 2021-02-04 오후 2 16 06" src="https://user-images.githubusercontent.com/67692759/106859328-3adda100-6706-11eb-908c-7092d1a9f1cc.png">
<img width="365" alt="스크린샷 2021-02-04 오후 3 29 36" src="https://user-images.githubusercontent.com/67692759/106859380-4a5cea00-6706-11eb-89a5-4555c26fab50.png">

