---
layout: post
title: "Vue 컴포넌트"
tags: [vue]
---

<br/><br/><br/>

## 컴포넌트 ?
`
컴포넌트란 조합하여 화면을 구성할 수 있는 블록을 의미합니다.
`

#### 특징
- 컴포넌트를 활용하면 화면을 빠르게 구조화하여 일괄적인 패턴으로 개발할 수 있다.
- 화면의 영역을 컴포넌트로 쪼개서 재활용할 수 있는 형태로 관리하면 다시 사용하기 편리함.
- 모든 사람들이 정해진 방식대로 컴포넌트를 등록하거나 사용하게 되므로 직관적으로 이해가능.


#### 전역 컴포넌트 등록

```
	Vue.component ('컴포넌트 이름' , {
    	// 컴포넌트 내용
    });
```

`
컴포넌트 등록 형식에는 컴포넌트 이름 , 컴포넌트 내용이 있습니다.
`

- 컴포넌트 이름은 template에서 사용할 HTML 사용자 정의 태그이름을 의미합니다.
- 태그 이름의 명명 규칙은 HTML 사용자 정의 태그 스펙에서 강제하는 '모두 소문자' 와 '케밥기법'
을 따르지 않아도 됩니다.

##### 케밥기법

`
변수가 단어의 조합으로 이루어져 있을때 단어와 단어사이를 -로 잇는 변수 명명 방식 ex ) my-compenent
`

#### 전역 컴포넌트 등록하기
![전역 컴포넌트](https://xlr3zz.github.io/assets/images/Component.PNG)


- 실행결과
![실행 결과](https://xlr3zz.github.io/assets/images/CompoResult.PNG)

#### 처리과정
1. 뷰 라이브러리 파일 로딩
2. 뷰 생성자로 컴포넌트 등록 Vue.component()
3. 인스턴스 객체 생성
4. 특정 화면 요소에 인스턴스 부착
5. 인스턴스 내용 변환 (등록된 컴포넌트 내용도 변환) mycomp에서 div로 변환됨
6. 변화된 화면 요소를 사용자가 확인


#### 지역 컴포넌트 등록

```
	new Vue({
    	components : {
        	'컴포넌트 이름' : 컴포넌트 내용
        }
    });
```

`
전역 컴포넌트와 달리 인스턴스에 components 속성을 추가하고 등록할 컴포넌트 이름과 내용을 정의하면 된다.
`

#### 지역 컴포넌트 등록하기
![지역 컴포넌트](https://xlr3zz.github.io/assets/images/localComponent.PNG)


- 실행 결과
![실행 결과](https://xlr3zz.github.io/assets/images/localResult.PNG)



#### 전역 컴포넌트와 지역 컴포넌트의 차이

![전역 컴포넌트와 지역 컴포넌트의 차이](https://xlr3zz.github.io/assets/images/compareComponent.PNG)

- 실행결과
![실행 결과](https://xlr3zz.github.io/assets/images/compareResult.PNG)

#### 결론
`
전역 컴포넌트는 한 번 등록하면 어느 인스턴스에서도 사용할 수 있다.
`
