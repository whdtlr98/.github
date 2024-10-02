# [🗺️ SeoulPOT 🗺️](http://43.202.163.51/)

<details>
  <summary><h2>🖥️ 2nd-agile</h2></summary>
  <p><strong>개발 기간</strong> | 2024-08-28 ~ 2024-09-27 (총 30일)</p>
  <p><strong>개발 목표</strong> | 웹 UI 개선 및 세부 기능(DA/AI) 구현</p>
  <p><strong>UI</strong> |</p>
  <img src="https://github.com/user-attachments/assets/d428f4f9-45a7-4846-b61b-8212f678dfad"  width="500"/>
  <img src="https://github.com/user-attachments/assets/69573f80-7116-4797-bcee-96d04105b48f"  width="500"/>
  <img src="https://github.com/user-attachments/assets/de32eb69-d2cc-4d88-a6a6-06fd64b5b7c7"  width="500"/>
  <img src="https://github.com/user-attachments/assets/38f1f3d1-c448-4243-bb31-04cc3c0458f0"  width="500"/>
</details>

<details>
  <summary><h2>🗂️ 요구사항 정의서</h2></summary>
  <details>
    <summary>프로젝트 관리</summary>
    <br/>
    <img src="https://github.com/user-attachments/assets/b65b1490-6401-498d-abca-9e04eba36e4e"  width="700"/>
  </details>
  <details>
    <summary>프론트엔드</summary>
    <br/>
    <img src="https://github.com/user-attachments/assets/0cdc5848-4fc1-4b54-b837-d68ab8f4fe5d"  width="700"/>
  </details>
  <details>
    <summary>백엔드</summary>
    <br/>
    <img src="https://github.com/user-attachments/assets/650722a1-e289-4a5e-b994-79b1561b7b66"  width="700"/>
  </details>
</details>

<details>
  <summary><h2>🎨 Figma</h2></summary>
  <img src="https://github.com/user-attachments/assets/fb2c4063-be07-425e-aaa3-1555c5d40259"  width="1000"/>
</details>

<details>
  <summary><h2>🌐 API 명세서</h2></summary>
  <img src="https://github.com/user-attachments/assets/0c888c07-6ebf-49cb-b826-894ee35fe41f"  width="700"/>
</details>

<details>
  <summary><h2>💾 데이터베이스 (ERD)</h2></summary>
  <img src="https://github.com/user-attachments/assets/225e5512-1f8e-4f03-958f-8c78f2edbc14"  width="700"/>
</details>

<details>
  <summary><h2>📅 일정 관리 (WBS)</h2></summary>
  <img src="https://github.com/user-attachments/assets/10018080-bc84-4ddd-a846-467723f404bd"  width="1000"/>
</details>


<details>
  <summary><h2>📚 아키텍쳐</h2></summary>
  <img src="https://github.com/user-attachments/assets/3672822f-8e68-49e6-90dd-4cd3338c1c05"  width="700"/>

</details>

<details>
  <summary><h2>🗨️ 후기</h2></summary>
  <p class="message">
      <strong>민정 : </strong>
      확실히 1차에 비해 성장한 저히들이 보입니다 🌟 마지막까지 화이팅 ❗
  </p>
  <p class="message">
      <strong>은진 : </strong>
      다같이 의지 활활 🔥 인 덕분에 저도 에너지를 얻고, 열심히 할 수 있었습니다~~
  </p>
  <p class="message">
      <strong>종식 : </strong>
      1차 때보다 성장했다는 느낌이 들었고 팀원들 모두가 진짜 개발자가 되어가는 듯한 모습에 희열을 느꼈습니다
  </p>
  <p class="message">
      <strong>해린 : </strong>
      처음에 목표했던대로 진행되고 있는 거 같아 아주 뿌듯하고 행복합니다 3차도 이 기세를 몰아 잘 마무리하고자 합니다 우리팀 첵오 😉 
  </p>
  <p class="message">
      <strong>건우 : </strong>
      최고의 팀원분들과 함께라서 프로젝트에 몰입할 수 있었습니다~~ 3차 때도 아자핑~💛
  </p>
  <p class="message">
      <strong>연규 : </strong>
      이번 2차에는 추석 연휴도 있어서 느슨해질 수도 있었는데, 다들 모여 열심히 해서 보람찼습니다. 앞으로 남은 3차까지도 이 기세를 몰아 끝까지 갔으면 좋겠습니다
  </p>
  <p class="message">
      <strong>승민 : </strong>
      중간에 합류해서 어려운 부분이 있을거라 생각했는데 다들 열정이 넘치셔서 금방 팀에 녹아들 수 있었습니다.
  </p>
  <p class="message">
      <strong>영빈 : </strong>
      다들 너무 열심히 하시는 모습이 저도 동기부여가 되었고 3차부터 조금이라도 도움이 되고싶습니다. 
  </p>
</details>

<details>
  <summary><h2>💣 이슈로그</h2></summary>
  <h3>⚠️ 이모지 인코딩 오류 [데이터베이스]</h3>
  <p><strong>문제:</strong> 리뷰 내용 데이터베이스 적재시 인코딩 문제로 인한 오류 발생</p>
  <p><strong>해결:</strong> utf8mb4로 character set을 변경해주어 이모지 적재가 가능하도록 함</p>
  <code>ALTER TABLE review_tb CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;</code>
  <br/><br/>
  <h3>⚠️ 팝업 데이터 크롤링 지연 문제 [크롤링]</h3>
  <p><strong>문제:</strong> 팝업 페이지를 크롤링 중 path값의 오류가 없음에도 크롤링이 진행되지 않는 문제 발생</p>
  <p><strong>해결:</strong> WebDriverWait를 바탕으로 리소스별 로딩 대기 시간을 주어 해결함</p>
  <br/>
  <h3>⚠️ 리뷰 크롤링 시 더보기 버튼 오류 [크롤링]</h3>
  <p><strong>문제:</strong> 리뷰 크롤링을 하다 보면 랜덤으로 몇몇 가게는 10개 이상의 리뷰가 있음에도 불구하고 더보기 버튼을 누르지 않아 10개의 리뷰만 긁어옴</p>
  <p><strong>해결:</strong> 원인 파악 중</p>
</details>


<details>
  <summary><h2>🔧 앞으로의 수정사항</h2></summary>
  <div class="section">
        <h4>✔️ 인공지능 모델 성능 강화</h4>
  </div>
  <div class="section">
        <h4>✔️ 추가 데이터 분석 수행 </h4>
  </div>
  <div class="section">
        <h4>✔️ 데이터 적재 방식 변경 (S3 + NoSQL)</h4>
  </div>
  <div class="section">
        <h4>✔️ 데이터 업데이트 자동화 및 병렬처리</h4>
  </div>
<br/>
</details>
