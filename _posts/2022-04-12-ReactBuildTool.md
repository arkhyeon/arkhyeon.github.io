---
layout: single
title: "React Build Tool"
excerpt: "vite : 빠름 / craco : 절대경로"

categories:
  - React
tags:
  - [React, buildtool, vite, craco]

toc: trues
toc_sticky: true
 
date: 2022-04-12
last_modified_at: 2022-04-12
---

```
vite 선택 이유 : build 시간의 불편을 느끼지 상대 경로에 대한 불편은 아직 없음
```

# Bundling

- node_modules 용량 큼
- import require 문법은 브라우저 친화적이지 않음
<img src="https://raw.githubusercontent.com/arkhyeon/JS/main/vite-project/mdimg/webpack.png">

# vite
$ npm create vite@latest  
yarn create vite
1. Vite 시작
    - 프로젝트의 성장에 따라 번들링 시간이 늘어남
    - Webpack의 빌드 속도는 느림

2. 빠른 이유
   - esbuild 를 사용하여 종속성을 미리 Bundle
<img src="https://vitejs.dev/assets/bundler.37740380.png">
   - 브라우저가 요청할 때 소스 코드를 변환, 제공 조건부 동적으로 가져오기에 뒤에 있는 코드는 현재 화면에서 실제로 사용되는 경우에만 처리됩니다.
<img src="https://vitejs.dev/assets/esm.3070012d.png">

# craco
yarn add @craco/craco
1. craco 시작
 - craco.config.js 파일 하나로 상대 경로가 아닌 절대 경로로 호출
2. 설정
```json
package.json

"scripts": {
    "start": "craco start",
    "build": "craco build",
    "test": "craco test" // or other Test
  },
```
3. 나머지 설정은 후기 폴더 확인 craco.config.js + babel.config.js
