# WEB
<details>
  <summary><h2>📂 공통 수정 사항</h2></summary>

### <mark>💾 로그 기록/mark>
> 사용자가 HTTP 요청을 할 떄 마다 해당 url과 변수들을 데이터 베이스에 저장을 하도록 함수를 만들어서 각 view 함수에서 사용.

### <mark>🚫 언어 필터링</mark>
> `re_path`를 사용하여 **한국어(kor)** 와 **영어(eng)** 이외의 언어로 된 URL 요청을 차단.  
> 정규식을 통해 URL의 시작 부분에서 언어를 판별하고, 허용되지 않은 언어의 요청은 처리되지 않도록 설정.

```python
from django.urls import re_path
from . import views

# URL 패턴에서 'kor' 또는 'eng'로 시작하는 요청만 허용
urlpatterns = [
    # 카테고리 선택 페이지
    re_path(r'^(?P<lang>\w{2,3})/$', category_choice, name='category_choice'),

    # place_tag_cd가 포함된 URL
    re_path(r'^(?P<lang>\w{2,3})/(?P<place_thema_cd>\w+)/$', district_view, name='district_view'),

    # 구 및 카테고리에 따른 장소 조회 (district_id와 place_category_cd 전달)
    re_path(r'^(?P<lang>\w{2,3})/(?P<district_id>\d+)/(?P<place_category_cd>\w+)/(?P<place_thema_cd>\w+)/$', category_district, name='category_district'),
]
```
</details>
<details>
  <summary><h2>📑 District 변경 사항</h2></summary>  

### 변경 내용
- 각 구의 설명을 간략화하여 간결하게 표시.
- 주요 관광지와 해당 관광지에 가까운 지하철역을 함께 표시.
- 설정한 5개의 구 외에 다른 구를 클릭할 경우, "Coming Soon" 메시지가 나타나도록 수정.

### 예시:
1. **강남구**:
   - **주요 관광지**: 봉은사, 코엑스
   - **가까운 지하철역**: 봉은사, 삼성
![image](https://github.com/user-attachments/assets/0c1a1705-de88-44f2-9a90-ac83e7631f48)

> 설정되지 않은 구를 클릭하면 "Coming Soon" 메시지가 표시됩니다.
> ![image](https://github.com/user-attachments/assets/07b66535-bfa2-40bc-8508-dca562197d12)

</details>

<details>
  <summary><h2>📑 Place 변경 사항</h2></summary>  

### 변경 내용
- **INFO창 추가**: 기존에 지도 마커가 어떤 장소를 나타내는지 알기 어려운 문제를 해결하기 위해 각 마커에 INFO창을 추가하여 장소 정보를 표시.
- **클릭 이벤트 수정**: 마커를 클릭하면 해당 장소의 리뷰 화면으로 이동하도록 수정.
- **즐겨찾기 기능 추가**: 장소가 많아 원하는 장소를 찾기 힘든 문제를 해결하기 위해, 즐겨찾기 기능을 도입. 사용자가 관심 있는 장소를 즐겨찾기에 추가하여 모아서 볼 수 있도록 수정.
- ![image](https://github.com/user-attachments/assets/eec8802e-3a2a-42dd-a4aa-83046457d53e)


</details>

<details>
  <summary><h2>📑 REVIEW 화면 변경 사항</h2></summary>  

### 변경 내용
- **리뷰 분석 서비스 도입**: 모든 리뷰를 보여주는 방식에서 벗어나, 고객들에게 리뷰를 더 효과적으로 제공하기 위해 모델을 통해 분석된 결과를 화면에 표시.
  - **긍정/부정 분석 결과**와 **광고성 비율**을 시각적으로 보여주도록 수정.
  
- **대표 리뷰 표시**: 최신순, 긍정, 부정 각각의 대표 리뷰 5개씩만 간단하게 요약하여 보여줌.
  - 모든 리뷰를 나열하지 않고, 중요한 리뷰들만 간략하게 확인 가능.

- **더보기 화면 추가**: 리뷰를 더 자세히 보고 싶은 경우를 대비하여 "더보기" 버튼을 추가하여, 클릭 시 전체 리뷰를 볼 수 있도록 수정.
  ![image](https://github.com/user-attachments/assets/22558165-0dc3-482d-8976-aca57b051c5b)

</details>

<details>
  <summary><h2>📑 카테고리 화면 변경 사항</h2></summary>  

### 변경 내용1
- **카테고리 버튼 구현**: 대표적인 9개의 카테고리를 버튼 형태로 화면에 배치. 사용자가 카테고리 버튼을 클릭하면 해당 카테고리의 장소 개수를 구별로 데이터베이스에서 읽어옴.
![image](https://github.com/user-attachments/assets/327b9577-3720-424f-9278-98808f78a696)

- **지도 시각화**: 각 구별로 해당 카테고리의 장소 개수를 지도 이미지에 반영하여, 색상으로 구분해 시각적으로 표현.
  - 각 구의 색상은 장소 개수에 비례하여 변화, 많은 장소를 포함하는 구일수록 더 진한 색으로 표시.
![image](https://github.com/user-attachments/assets/68fc2baf-17a4-43e2-800e-b36d84c17eb2)

</details>
