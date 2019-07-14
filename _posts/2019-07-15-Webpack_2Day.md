---
layout: post
title: "Webpack 2Day"
tags: [webpack]
---

***

`
Webpack Loader
`
- 웹팩은 자바스크립트 파일만 처리가 가능하도록 되어 있다.
- loader를 이용하여 다른 형태의 웹 자원들을(img,css 등) js로 변환하여  
  로딩이 가능하다.

```
1  module.exports = {
2      entry : {
3        // ...
4      },
5      output : {
6        // ...
7      },
8      module : {
9          rules : [
10            {
11                  test : /\.css$/
12                , use  : ['style-loader' , 'css-loader']
13            }
14          ]
15      }
16  };
```

> 11라인 - 확장자명이 css인 모든 파일에 대해서  
> 12라인 - style-loader , css-loader를 사용하겠다

`
loader에서 모듈 로딩 순서는 배열의 요소 오른쪽에서 왼쪽으로 진행된다.
`

```
{
    test : /backbone/
  , use  : [
        'expose-loader?Backbone'
      , 'imports-loader?_=underscore,jquery'  
      // 순서대로 (1) jquery , (2) underscore 로딩
      // expose-loader , imports-loader 는 nodejs에서..!
  ]
}
```

`
위 설정 파일을 webpack 으로 번들링 한 결과물은 아래와 같다.
`

```
  var __WEBPACK_AMD_DEFINE_ARRAY__, __WEBPACK_AMD_DEFINE_RESULT__;
  var _ = __webpack_require__(0);
  var jquery = __webpack_require__(1);
```

***

`
Babel Loader - ES6
`

- preset : Babel 플러그인 리스트

```
  module : {
    rules : [{
        test : /\.js$/
      , use  : [{
          loader  : 'babel-loader'
        , options : {
            presets : [
              ['es2015' , 'react' , {modules : false}]
            ]
        }  
      }]  
    }]
  };
```

```
   .bablerc < 파일명

   {
     "presets" : ["react" , "es2015"]
   }

```

`
위와 같이 미리 설정 가능
`
