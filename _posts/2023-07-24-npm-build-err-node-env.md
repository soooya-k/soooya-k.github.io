---
title: "ERROR : 'node_env'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다."
date: 2023-07-24 21:31:00 +0900
categories: [문제 해결, 문제 해결_npm]
tags: [npm, node, node.js]
---
## 재현 경로

Windows에서 Github blog의 jekyll 테마 빌드를 위한 `npm run build` 실행 중 발생한 에러.

<br />

## 해결
```
npm install -g win-node-env
```

