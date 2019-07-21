---
layout: post
title: "Webpack 3Day"
tags: [webpack]
---

***

`
Plugin
`

> 파일별 커스텀 기능을 사용하기 위해 사용.  
> Loader = 웹팩으로 번들링을 하면서 처리할 때 중간에 개입  
> Plugin은 번들링이 끝나고 결과값을 낼 때 개입

```
  module.exports = {
      entry  : {} ,
      output : {} ,
      module : {} ,
      plugin : [
        new webpack.optimize.UglifyJsPlugin()
      ]
  }
```

`
ProvidePlugins
`

> 모든 모듈에서 사용할 수 있도록 해당 모듈을 변수로 변환한다.

```
  new webpack.ProvidePlgin({
      $ : "jquery"
  })
```

`
DefinePlugin
`

> Webpack 번들링을 시작하는 시점에 사용 가능한 상수들을 정의.  
> 일반적으로 개발계 & 테스트계에 따라 다른 설정을 적용할 때 유용하다.

```
  new webpack.DefinePlugin({
      PRODUCTION : JSON.stringify(true) ,
      VERSION    : JSON.stringify("5fa3b9"),
      BROWSER_SUPPORTS_HTML5 : true ,
      TWO : "1+1" ,
      "typeof window" : JSON.stringify("object")
  })
```

`
ManifestPlugin
`

> 번들링시 생성되는 코드 ( 라이브러리 )에 대한 정보를 JSON파일로 저장하여 관리

```
  new ManifestPlugin({
      fileName : 'manifest.json'  ,
      basePath : './dist/'
  })
```
