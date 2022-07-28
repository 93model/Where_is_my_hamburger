## Whee is my Hamburger


## 🛠 문제
나는 햄버거를 매우 좋아한다.
하지만 내가 사는 지역( 가락본동 )에는 햄버거 프랜차이즈 전문점이 단 한 개도 없다. 
![캡처](/image/garak.png)

최소 도보로 30분 이상 떨어진 지역에만, 햄버거 가게가 있다. 

도대체 왜 그런지 궁금해져서 공공데이터를 활용해 분석

개발 환경
Google Colab Pro ( GPU : T4, P100 / RAM : 최대 25.51GB / CPU : Intel® Xeon® CPU @ 2.30GHz )
시각화 툴 : Folium (Seoulmaps Geojson 활용 https://github.com/southkorea/seoul-maps)

## ❓ 데이터 선정
가설 : 거주인구, 유동인구, 성비, 65세 이상 노인 비율이 영향을 줄 것이다. 
공공 데이터 : 서울시 행정동 426개동 
서울시 거주 인구 데이터 : 인구수, 성비, 65세 이하 비율(https://data.seoul.go.kr/dataList/10043/S/2/datasetView.do)

서울시 5월 생활인구 데이터 (https://data.seoul.go.kr/dataList/OA-14991/S/1/datasetView.do)

소상 공인 데이터 : 행정동 별 햄버거 전문점의 갯수
맥도날드, 롯데리아, 버거킹, 맘스터치, KFC, 노브랜드 버거,
프랭크 버거, 파파이스, 쉐이크쉑 (https://www.data.go.kr/data/15083033/fileData.do)

## 🧹 데이터 시각화
서울시 프랜차이즈별 햄버거 전문

![캡처](/image/ham_count.png)


행정동별 주민 등록 인구

![캡처](/image/residence_peo.png)

행정동별 22.05 생활인구 평균

![캡처](/image/living_peo.png)

행정동별 햄버거 전문점

![캡처](/image/dong_ham.png)




## 🔍 데이터 분석
랜덤포레스트 + RamdomCV모델이 가장 정확도가 좋았다.
하지만 feature가 4개에 행정동별로 426개 밖에 없어서 예측력이 좋지는 않다.

(테스트 정확도 : 0.4113)

![캡처](/image/feature_importance_ham.png)

Feature importance 분석 결과
생활인구의 영향이 가장크다.

## ✔️ 결과
그러나 내가 사는 가락본동의 경우 거주인구도 평균에 비해 높지만, 주변지역에 비해 거주인구가 조금 떨어진다.
생활인구가 평균에 비해  높다. 
단 주변 지역에 비해, 성비가 높고, 65세이하 비율이 조금 낮다

예상과는 다른 결과
- 가락본동은 주변보다 생활인구가 많지만, 햄버거 전문점은 없다.
    - 그럼 **가락본동에는 햄버거 전문점에 생기면 장사가 잘된다**
    - 그리고 결국, 이 프로젝트 진행 중에 현재 공격적인 마케팅과 확장을 하고 있는  ‘프랭크 버거 송파가락점’이 생겼고 개점 일주일만에 네이버지도 방문리뷰 100개를 넘었다



