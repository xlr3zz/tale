---
layout: post
title: "Vue 생명주기"
tags: [vue]
---


#### 뷰 라이프 사이클 다이어그램
![Life Cycle](https://xlr3zz.github.io/assets/images/lifeC.jpg)


#### 라이프 사이클 설명

- beforeCreate
```
인스턴스가 생성되고 가장 처음으로 실행되는 라이프 사이클
data속성과 methods속성이 인스턴스에 정의되어 있지 않고, 돔과 같은 화면 요소에도
접근이 가능한 단계입니다.
```
- created
```
data속성과 methods속성이 정의되었기 때문에 로직들을 이용하여 data속성과
methods속성에 의된 값에 접근하여 로직을 수행할수 있는 단계입니다.
```
- beforeMount
```
created 이후에 template 속성에 지정한 마크업 속성을 render() 함수로변환한 후
el속성에 지정한 화면 요소에 인스턴스를 부착하기 전에 호출되기 때문에 화면에
붙이기 전에 실행해야 할 로직을 추가하기 좋은 단계입니다.
```
- mounted
```
el속성에서 지정한 화면 요소에 인스턴스가 부착되고 나면 호출되는 단계로, 화면 요소
(돔)에 접근할 수 있어 화면 요소를 제어하는 로직을 수행하기 좋은 단계입니다.
```
- beforeUpdate
```
el 속성에서 지정한 화면 요소에 인스턴스가 부착되고 난 후에 인스턴스 속성들이
화면에 치환됩니다. 이 치환된 값을 $watch 속성으로 감시하고, 데이터 관찰이라고
합니다.이렇게 관찰하고 있는 데이터들이 변경되면 가상 돔을 이용해 화면에 다시
그려야 합니다.이 때,그리기 직전 호출되는 단계가 beforeUpdate 입니다.
따라서 변경 예정인 데이터 값을 이용해 작업을 해야할 때 그 로직을 구현하기
좋은 단계입니다.
```
- updated
```
데이터가 변경되고 나서 가상 돔으로 다시 화면을 그리고 나면 실행되는 단계이므로,
데이터 변경 이후 화면 요소 제어와 관련된 로직을 추가하기 좋은 단계입니다.
이 단계에서 데이터 값을 변경하면 무한루프에 빠질 수 있기 때문에 값을 변경하려면
computed,watch와 같은 속성을 사용해야 합니다.
```
- beforeDestroy
```
뷰 인스턴스가 파괴되기 직전에 호출되는 단계입니다. 이 단계에서는 아직 인스턴스에
접근할 수 있습니다. 즉 뷰 인스턴스의 데이터를 삭제하기 좋은 단계입니다.
```
- destroyed
```
뷰 인스턴스가 파괴되고나서 호출되는 단계입니다. 뷰 인스턴스에서 정의한 모든 속성이
제거되고 하위에 선언한 인스턴스들 또한 모두 파괴됩니다.
```

#### 라이프 사이클 예제
![Life Cycle Ex](https://xlr3zz.github.io/assets/images/LifeEx1.PNG)

- 실행결과
```
beforeCreate
created
mounted
```
<br/>

![Life Cycle Ex](https://xlr3zz.github.io/assets/images/LifeEx2.PNG)

- 실행결과
```
beforeCreate
created
mounted
updated
```

`
mounted에서 데이터 변경 유무에 따라서 updated가 호출한다.
`

