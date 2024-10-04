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
    <img src="https://github.com/user-attachments/assets/6b4b7950-7f44-4ef2-9953-ef52f48b007d"  width="700"/>
  </details>
  <details>
    <summary>웹</summary>
    <br/>
    <img src="https://github.com/user-attachments/assets/4cdc82e6-33e7-43b0-86b6-55803966eefd"  width="700"/>
  </details>
  <details>
    <summary>DA-AI</summary>
    <br/>
    <img src="https://github.com/user-attachments/assets/ec5277a7-857d-4afd-9a8c-8260fac4ecd5"  width="700"/>
  </details>
</details>

<details>
  <summary><h2>🎨 Figma</h2></summary>
  <img src="https://github.com/user-attachments/assets/2690d5dc-ad47-476b-b454-854024d994f7"  width="1000"/>
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
  <h3>⚠️ LLM 구동시 RAM 부족 [인공지능]</h3>
  <p><strong>문제:</strong> 구글 코랩의 T4 GPU로 Llama2-7B 사용시 RAM의 부족으로 런타임 종료</p>
  <p><strong>해결:</strong> 코랩에서 작동 가능한 경량화된 Mistral-7B 사용 (추론, 이해, STEM 추론에서 Llama 2와 비교하여 3배 이상 작은 사이즈로 더 좋은 성능을 보여줌)</p>
  <br/>
  <h3>⚠️ ecs 컨테이너가 용량 문제로 강제종료 [웹 aws]</h3>
  <p><strong>문제:</strong> ecs task 정의 시 할당한 cpu와 메모리가 부족해 컨테이너가 강제종료됨</p>
  <p><strong>해결:</strong> task 메모리 및 cpu 크기를 늘림</p>
  <br/>
  <h3>⚠️ 코드 변경 있을 때마다 새로운 task 생성으로 ip주소 바뀜 [웹 aws]</h3>
  <p><strong>문제:</strong> 코드 변경 있을 시 pipeline을 통해 새로운 버전의 task 생성으로 서비스 ip 주소 새로 생성</p>
  <p><strong>해결:</strong> 로드 밸런싱을 통해 해결 예정</p>
  <h3>⚠️ 페이지네이션 시 기존 웹페이지 기능 미적용 [웹개발]</h3>
  <p><strong>문제:</strong> 모달창 기능, 데이터베이스 로드 기능이 구현되지 않는 오류</p>
  <p><strong>해결:</strong> 자바스크립트 코드에 페이지네이션 적용 시 모달창 함수와 데이터가 로드가 될 수 있는 함수 적용</p>
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
