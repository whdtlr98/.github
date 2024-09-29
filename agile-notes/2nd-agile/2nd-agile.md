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
  <img src="https://github.com/user-attachments/assets/e343cb3c-92a6-47d0-b32c-e4a7c96012ca"  width="700"/>
</details>

<details>
  <summary><h2>💾 데이터베이스 (ERD)</h2></summary>
  <img src="https://github.com/user-attachments/assets/225e5512-1f8e-4f03-958f-8c78f2edbc14"  width="700"/>
</details>

<details>
  <summary><h2>📅 일정 관리 (WBS)</h2></summary>
  <img src="https://github.com/user-attachments/assets/47869252-8e11-4d3c-b94a-28ad6ba91b33"  width="1000"/>
</details>
<details>
  <summary><h2>📚 아키텍쳐</h2></summary>
  <img src="https://github.com/user-attachments/assets/5d6c3b37-1fb1-408e-80d2-9fe9567130cb"  width="700"/>

</details>

<details>
  <summary><h2>🗨️ 후기</h2></summary>
  <p class="message">
      <strong>민정 : </strong>
      확실히 1차에 비해 성장한 저히들이 보입니다 🌟 마지막까지 화이팅 ❗
  </p>
  <p class="message">
      <strong>은진 : </strong>
      룰루랄라 2차도 화이팅 :) (이게 toy가 맞나요?)
  </p>
  <p class="message">
      <strong>종식 : </strong>
      1차 때보다 성장했다는 느낌이 들었고 팀원들 모두가 진짜 개발자가 되어가는 듯한 모습에 희열을 느꼈습니다
  </p>
  <p class="message">
      <strong>해린 : </strong>
      분명 1차때 다 할 수 있을 줄 알았는데 2,3차로 넘어가버리는 마술 … ? 🧙🏻
  </p>
  <p class="message">
      <strong>건우 : </strong>
      최고의 팀원분들과 함께라서 프로젝트에 몰입할 수 있었습니다~~ 3차 때도 아자핑~💛
  </p>
  <p class="message">
      <strong>연규 : </strong>
      프론트 어질어질해요 😂
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
        <h3>✔️ 외국인 방문객에 적합한 5개 구 리뷰 크롤링</h3>
        <ul>
            <li>강남구</li>
            <li>중구</li>
            <li>종로구</li>
            <li>마포구</li>
            <li>용산구</li>
        </ul>
    </div>
  <br/>
    <div class="section">
        <h3>✔️ 체크박스 및 각종 프론트 수정</h3>
        <img src="https://github.com/user-attachments/assets/e02bd58e-158e-4453-ba61-5f1ad27ae88e" alt="프론트 수정 이미지" style="width: 400px;">
    </div>
    <div class="section">
        <h3>✔️ 추가 관광지 정보 조사 후 추가 예정</h3>
        <ul>
            <li>현재 관광지에 구별 2-3개 관광지만 존재함</li>
        </ul>
    </div>
<br/>
</details>
