---
layout: post
title: "Webpack Entry"
tags: [webpack]
---

***
`
Entry
`
- webpack으로 묶은 모든 라이브러리들을 로딩할 시작점 설정
- a,b,c 라이브러리를 모두 번들링한 bundle.js를 로딩한다.
- 1개 또는 2개 이상의 엔트리 포인트를 설정할 수 있다.

`
Outout
`
- 대상의 파일을 번들링해서(웹팩을 돌려서) 나온 결과물의 위치를 의미

```
 {
   entry : '.public/src/index.js' ,   // String

   output : {
      path : '/dist' ,
      filename : 'bundle.js'
   }
 }  


 {
   entry : ['.public/src/index.js'],   // Array

   output : {
      path : '/dist' ,
      filename : 'bundle.js'
   }
 }


 {
   entry : {
     '.public/src/index.js'   // Object
   },
   output : {
      path : '/dist' ,
      filename : 'bundle.js'
   }
 }
```

***

`여러가지 Entry 유형`
```
  var config = {
      // #1 - 간단한 entry 설정
      entry : './path/to/my/entry/file.js'

      // #2 - 앱 로직용 , 외부 라이브러리용
      entry : {
          app : './src/app.js' ,
          vendors : './src/vendors.js'
      }

      // #3 - 페이지당 불러오는 js 설정
      entry : {
          pageOne : './src/pageOne/index.js' ,
          pageTwo : './src/pageTwo/index.js' ,
          pageThr : '/src/pageThr/index.js'
      }
  }
```

***

`복수 엔트리 포인트 설정 예시`
```
  webpack.config.js

  module.exports = {
      // 시작점
      entry : {     
          Profile : './profile.js' ,
          Feed : './feed.js'
      },
      // 결과물
      output : {
          path : 'bulid' ,
          filename : '[name].js'  // 위에 지정한 entry 키의 이름에 맞춰서 결과 산출
      }
  }

  // 번들파일 Profile.js 를 <script src="bulid/Profile.js"></script>로 HTML에 삽입
```

***

`Output Name 옵션`

```
  output : {
      filename : '[name].js' ,
      filename : '[hash].js' ,
      filename : '[chunkhash].js'
  }
```
1. [name] : 엔트리 명에 따른 output 파일명 생성
1. [hash] : 특정 webpack build에 따른 output 파일명 생성
1. [chunkhash] : 특정 webpack chunk에 따른 output 파일명 생성

***

### 참고 API

`
  path.join()
`

- 해당 API가 동작되는 OS의 파일 구분자를 이용하여 파일 위치를 조합한다.

```
  path.join('/foo','bar','baz/asdf');

  결과 : '/foo/bar/baz/asdf'  
```  

`
  path.resolve() - 안전한 번들링을 위해 사용
`
- join() 의 경우 그냥 문자열을 합치지만 ,  
resolve는 오른쪽에서 왼쪽으로  파일 위치를 구성해가며 유효한 위치를 찾는다.
- 만약 결과값이 유효하지 않으면 현재 디렉토리가 사용된다.   
반환되는 위치 값은 항상 absolute URL이다.

```
  path.resolve('/foo/bar', './baz');
  결과 : '/foo/bar/baz'

  path.resolve('/foo/bar', '/tmp/file/');
  결과 : '/tmp/file'

  path.resolve('wwwroot', 'static_files/png/', '../gif/image.gif');
  결과 : /home/myself/node/wwwroot/static_files/gif/image.gif

```
