# wanted-codestates-project-7-11
사용자가 입력한 **성향 진단 결과값**을 기업 성향 진단 결과와 비교하여 **그래프**로 보여주는 서비스입니다. 

## 사용한 기술 스택
<img src="https://img.shields.io/badge/Vue-40B983.svg?&style=for-the-badge&logo=React&logoColor=fff"/> <img src="https://img.shields.io/badge/SCSS-CE699B.svg?&style=for-the-badge&logo=SASS&logoColor=fff"/> <img src="https://img.shields.io/badge/Chart.js-FF787C.svg?&style=for-the-badge&logo=Chart.js&logoColor=fff"/> 

## 프로젝트 실행 방법

- 배포 사이트 : https://personality-test.surge.sh/
- 로컬 :  
1. `git clone https://github.com/Pre-Onboarding-FE-Team07/wanted-codestates-project-7-11.git`
2. `npm install`
3. `npm run dev`

   
## 프로젝트 구조

```
--📁 src
  ---📁 assets : 이미지 asset 폴더 
  ---📁 components : 컴포넌트 폴더
  ---📁 data : 데이터 폴더
  ---📁 scss: scss style 파일 폴더
  ---📁 utils: 모듈화된 함수 폴더
```

## 팀 멤버

| 이름                                       | 직책 | 역할                                       |
| ------------------------------------------ | ---- | ----------------------------------- |
| [🔨이예지](https://github.com/Lee-ye-ji)   | 팀원| 개발 환경 구축 및 바차트 구현 |
| [⚡️박진용](https://github.com/jinyongp)   | 팀원 |  추천 검색어 기반 검색창 구현    |       
| [🎨문선경](https://github.com/dev-seomoon) | 팀원 | 개발 환경 설정 및 펜타곤 차트 구현       |
| [✏️예효은](https://github.com/ye-yo)       | 팀원 |   도넛 차트 구현          |
| [🚀심채윤](https://github.com/Lela12)      | 팀장 |      헤더 및 탭 컴포넌트 구현        |


---

## 구현한 기능 목록
- 추천 검색어 기반 검색창
- 펜타곤 차트
- 탭 클릭을 통한 차트 데이터 변경
- 바 차트
- 도넛차트(추가 구현)
---


## 이예지

#### 구현한 방법

#### 어려웠던 점 (에러 핸들링)


## 박진용

#### 구현한 방법

#### 어려웠던 점 (에러 핸들링)


## 문선경

### 구현한 방법

### 어려웠던 점 (에러 핸들링)


## 예효은
선택한 기업과의 매칭률을 보여주는 도넛 차트 구현

### 구현한 방법
차트 구현을 3명이서 진행하게 되어 저는 추가로 새로운 차트를 만들어보기로 했습니다. radar, bar 차트 외에 여러 가지 차트 중 도넛 차트가 현재 보유한 데이터로 표현하기 좋을 것 같아 선택하였습니다. 도넛 차트에 표현할 데이터는 고심끝에 현재 선택한 기업과의 매칭률을 보여주는 것으로 결정했고, 다른 차트가 선택한 기업에 따라 변화하는 차트임으로 저 역시 유사하게 동작할 수 있도록 차트 주제를 결정하였습니다. 
`setup` 이라는 Composition API를 사용하여 내부에서 `computed`,`watch` 메소드등을 모두 사용할 수 있었고, 이를 활용하여 기업 데이터가 변경될 때마다 매칭률을 계산하여 차트를 재렌더링 하도록 만들었습니다.
매칭률은 `a / b * 100`으로 계산할 수 있으므로 각 항목(aggressive, confident 등..)별로 계산한 뒤, `항목별 나눗셈 결과합 / 항목의 개수 * 100`과 같은 계산 방식으로 매칭률을 도출했습니다. 또한 사용자의 점수가 기업의 점수보다 높을 경우 나눗셈 결과값이 1이 넘어 최종 매칭률이 100%가 넘을 수 있기 때문에 1이 넘어가는 값에 대해 값을 조정하는 등의 추가적인 연산을 거쳤습니다.


### 어려웠던 점 (에러 핸들링)
#### 1. vue.js, chart.js, scss 사용
`Vue.js` 및 `SCSS`는 이전에 to-do list 구현을 개인적으로 해 본 경험이 있는데 이번에 다시금 공부해보게 되었습니다. chart.js의 경우 자바스크립트 웹 사이트 개발 시에 사용해보았었는데 vue에서 사용하기 위해서는 추가적으로 `vue-chartjs`라는 라이브러리 설치가 필요했고 사용해보니 `vue-chartjs`가 최신 버전의 vue3를 지원하지 않는다는 것을 알게되어 이를 지원하는 `vue-chart-3` 라이브러리를 사용하였습니다.

#### 2. 코드 리팩토링
처음 차트 컴포넌트 구현 시에는 `setup`함수를 사용하지 않고 `methods`, `watch` 등의 함수들을 사용하여 구현했었습니다. 보다 익숙한 함수들을 사용해서 구현을 완료하였으나 `vue-chart-3` 공식문서의 예제코드에서는 `setup` 함수를 사용한 것을 보고 어떤 함수인지 궁금하여 개인적으로 찾아보게되었습니다. 그러다 `setup`이라는 함수는 `vue3`부터 등장한 composition API 중 하나이며 이전 버전에서 `data, methods, watch, computed`를 별도로 작성하는 것을 `setup`함수 내에서 하나로 모아 작성이 가능하다는 것을 알게되었습니다. 이미 코드를 완성하긴 했지만 이번에 Vue3를 사용하였기 때문에 최신 버전의 장점을 활용해보자는 마음도 있었고, `setup` 함수의 기능 자체가 무척 흥미로워서 코드를 리팩토링해보게 되었습니다. 

직접 구현해보니 `setup` 함수 내에서 `computed watch` 등의 함수 등을 사용하는 것은 무척 간단했고, 컴포넌트에서 사용할 데이터를 `ref`, `reactive` 로 선언하여 마지막에 return 해준다는 것이 중요하게 생각되었습니다. `ref`와 `reactive`는 모두 변경사항이 추적되는 반응 개체를 만들기 위한 방식으로 `ref`는 숫자, 문자열, boolean 값을, `reactive`는 object를 저장하기 위해 사용되기 때문에 이를 활용하여 `matchRate`나 `chartData` 등을 저장하여 처리하였습니다.

#### 3. 차트 반응형
차트가 윈도우 리사이징에 따라 줄어든 후 윈도우 사이즈가 확장되어도 다시 사이즈가 조정되지 않는 문제가 있어 원인 분석 및 해결방법을 찾아보았습니다. 
반응형을 위한 `responsive`값은 default가 `true`이기 때문에 문제가 없었으며 리사이징 시의 종횡비 유지 옵션인 `maintainAspectRatio`를 `false` 로 변경해주어야 한다는 것을 알게되었습니다. 종횡비 유지 옵션을 false로 설정할 경우 차트의 사이즈가 상위 컨테이너 요소의 사이즈에 따라 자동 조정되어 원하는 결과를 얻을 수 있었습니다.


## 심채윤

#### 구현한 방법

#### 어려웠던 점 (에러 핸들링)
