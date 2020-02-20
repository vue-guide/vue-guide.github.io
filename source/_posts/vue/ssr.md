---
title: 서버사이드 렌더링
toc: true
date: 2019-05-03 19:04:47
tags:
	- Vue.js
categories:
	- Vue.js
---

## 완전한 서버사이드 렌더링(SSR) 가이드

서버사이드 렌더링을 사용하는 Vue 애플리케이션을 만들기 위한 독립적인 가이드를 만들었습니다. 이는 클라이언트 Vue와 서버 측 Node.js 개발 및 웹팩에 익숙한 사람들을 위한 매우 깊이 있는 가이드입니다. [ssr.vuejs.org](https://ssr.vuejs.org/)에서 확인하세요.

## Nuxt.js

배포 준비 완료 상태의 서버측 렌더링을 사용하는 애플리케이션을 올바르게 구성하는 것은 어려운 작업입니다. 다행히 이 모든 것을보다 쉽게하기 위한 훌륭한 커뮤니티 프로젝트가 있습니다. [Nuxt.js](https://nuxtjs.org/)입니다. Nuxt.js는 Vue 생태계 위에 만들어진 상위 수준의 범용 Vue 애플리케이션을 작성하는 데 매우 간소화 된 개발 환경을 제공합니다. 더 나아가 정적 사이트 생성기(단일 파일 Vue 컴포넌트로 작성된 페이지 포함)로 사용할 수도 있습니다. 한번 시도해보세요

## Quasar Framework SSR + PWA

[Quasar Framework](https://quasar.dev) will generate an SSR app (with optional PWA handoff) that leverages its best-in-class build system, sensible configuration and developer extensibility to make designing and building your idea a breeze. With over one hundred specific "Material Design 2.0"-compliant components, you can decide which ones to execute on the server, which are available in the browser - and even manage the `<meta>` tags of your site. Quasar is a node.js and webpack based development environment that supercharges and streamlines rapid development of SPA, PWA, SSR, Electron and Cordova apps - all from one codebase.
