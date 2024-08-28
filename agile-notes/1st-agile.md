# [🗺️ SeoulPOT 🗺️](http://13.125.231.69/)
<details>
  <summary><h2>🖥️ 1st-agile : SeoulPOT</h2></summary>
  <p><strong>개발 기간</strong> : 2024-07-23 ~ 2024-08-27 (총 30일)</p>
  <img src="https://github.com/user-attachments/assets/e343cb3c-92a6-47d0-b32c-e4a7c96012ca"  width="700"/>
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
  <img src="https://github.com/user-attachments/assets/aabf7ec0-16c3-4b35-b4ec-ec9fd7e155bf"  width="700"/>
</details>

<details>
  <summary><h2>📅 일정 관리 (WBS)</h2></summary>
  <img src="https://github.com/user-attachments/assets/3d94314a-aa08-4438-8469-f9a1f350c4a9"  width="1000"/>
</details>

<details>
  <summary><h2>🗨️ 후기</h2></summary>
  <p class="message">
      <strong>민정 : </strong>
      🌈 3차까지 할 수 있을까요? 가 아니라 해야죠 화이팅 !
  </p>
  <p class="message">
      <strong>은진 : </strong>
      룰루랄라 2차도 화이팅 :) (이게 toy가 맞나요?)
  </p>
  <p class="message">
      <strong>종식 : </strong>
      언제쯤 1인분을 할 수 있을까..?
  </p>
  <p class="message">
      <strong>해린 : </strong>
      분명 1차때 다 할 수 있을 줄 알았는데 2,3차로 넘어가버리는 마술 … ? 🧙🏻
  </p>
  <p class="message">
      <strong>건우 : </strong>
      저는 행복해요😊
  </p>
  <p class="message">
      <strong>연규 : </strong>
      프론트 어질어질해요 😂
  </p>
</details>

<details>
  <summary><h2>💣 이슈로그</h2></summary>
  <br/><br/>
  <p><strong>⚠️ 이모지 인코딩 오류 [데이터베이스]</strong></p>
  <p><strong>문제:</strong> 리뷰 내용 데이터베이스 적재시 인코딩 문제로 인한 오류 발생</p>
  <p><strong>해결:</strong> utf8mb4로 character set을 변경해주어 이모지 적재가 가능하도록 함</p>
  <code>ALTER TABLE review_tb CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;</code>
  <br/><br/>
  <p><strong>⚠️ 운영시간의 큰 형식 차이 [데이터 전처리]</strong></p>
  <p><strong>문제:</strong> 요일마다 있는 곳도 있으며, 시간만 있는 곳도 있었으나 하나의 형식으로 맞추어야 했음</p>
  <p><strong>해결:</strong> 요일마다 있더라도 대부분의 시간대가 동일하므로, 00:00 ~ 00:00 형식의 데이터 추출( & 정기 휴무)로써 통일화</p>
  <br/><br/>
  <p><strong>⚠️ 전처리 코드 통일화 필요 [데이터 전처리]</strong></p>
  <p><strong>문제:</strong> 크롤링을 분담하여 수행하다보니, 데이터 형식의 차이 존재</p>
  <p><strong>해결:</strong> encoding : utf-8로 통일, 컬럼명 통일 과정 거침 (하나의 코드로 전처리 가능하도록)</p>
  <br/><br/>
  <p><strong>⚠️ datetime type error [데이터 전처리]</strong></p>
  <p><strong>문제:</strong> Python의 timestamp가 MySQL로 들어가지 못함</p>
  <code>>> Python 'timestamp' cannot be converted to a MySQL type</code>
  <p><strong>해결:</strong> timestamp를 datetime으로 변환하여 적재 (pd.to_datetime 활용)</p>
  <br/><br/>
  <p><strong>⚠️ 지도 시각화 버튼 인식 오류 [프론트엔드]</strong></p>
  <p><strong>문제:</strong> 서울시의 중심이 기준으로 인식되어 버튼 호버→ 확대시 좌우, 상하 이동 발생</p>
  <p><strong>해결:</strong> 구의 각 요소에 중심값을 설정하여 시각적으로 잘 확대되도록 해결</p>
  <br/><br/>
  <p><strong>⚠️ 지도 클릭이 안되는 오류 [크롤링]</strong></p>
  <p><strong>문제:</strong> 네이버 페이지 특성 상 Iframe으로 감싸져 있어 페이지 클릭이 안되는 오류 발생</p>
  <p><strong>해결:</strong> 네이버 지도에서 가게 코드를 따와 모바일 버전 링크로 1차 크롤링 후 가게 정보, 리뷰에 대한 2,3차 크롤링 진행</p>
  <br/><br/>
  <p><strong>⚠️ 리뷰에 포함된 각종 태그 인식 오류 [크롤링]</strong></p>
  <p><strong>문제:</strong> 원하는 태그를 가져올 때 제대로 인식이 안되서 에러 발생</p>
  <p><strong>해결:</strong> 태그를 따로 지정해놓은 후 같은 태그가 있으면 저장하는 방법 사용</p>
  <br/><br/>
  <p><strong>⚠️ 리뷰가 없는 가게 인식 문제 [크롤링]</strong></p>
  <p><strong>문제:</strong> 리뷰가 없는 가게 무한 페이지 다운 오류 발생</p>
  <p><strong>해결:</strong> break, continue 를 사용했을 때 정상적인 가게들의 리뷰 크롤링 마저 문제가 생겨 리뷰가 없는 가게 행 삭제</p>
  <br/><br/>
  <p><strong>⚠️ 식당 정보 데이터 문제 [크롤링]</strong></p>
  <p><strong>문제:</strong> 서울시 식당 정보 데이터를 받아왔으나, 프랜차이즈나 가게 명으로만 검색할 경우 여러개의 가게가 검색되거나 혹은 해당 가게가 검색되지 않는 오류 발생</p>
  <p><strong>해결:</strong> 가게명과 주소 일부를 같이 작성해 검색함</p>
  <br/><br/>
  <p><strong>⚠️ 식당 정보 데이터 문제 [크롤링]</strong></p>
  <p><strong>문제:</strong> 폐업한 가게를 제외하고 검색했으나 해당 가게가 존재하지 않는 이슈 발생</p>
  <p><strong>해결:</strong> 1차 애자일에서는 주소값이 없는 가게를 제외하고 크롤링 → 주소값이 없는 가게를 2차 크롤링을 할 지, 없는 가게로 칭할 지 아직 미정</p>
  <br/><br/>
  <p><strong>⚠️ 팝업 데이터 크롤링 지연 문제 [크롤링]</strong></p>
  <p><strong>문제:</strong> 팝업 페이지를 크롤링 중 path값의 오류가 없음에도 크롤링이 진행되지 않는 문제 발생</p>
  <p><strong>해결:</strong> WebDriverWait를 바탕으로 리소스별 로딩 대기 시간을 주어 해결함</p>
  <br/><br/>
  <p><strong>⚠️ 리뷰 크롤링 시 더보기 버튼 오류 [크롤링]</strong></p>
  <p><strong>문제:</strong> 리뷰 크롤링을 하다 보면 랜덤으로 몇몇 가게는 10개 이상의 리뷰가 있음에도 불구하고 더보기 버튼을 누르지 않아 10개의 리뷰만 긁어옴</p>
  <p><strong>해결:</strong> 원인 파악 중</p>
</details>
