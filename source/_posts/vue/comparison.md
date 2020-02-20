---
title: 다른 프레임워크와의 비교
toc: true
date: 2019-02-20 19:04:47
tags:
	- Vue.js
categories:
	- Vue.js
---

이 섹션은 작성하기 가장 까다로운 페이지이지만, 중요하다고 생각합니다. 당신은 해결하려는 문제가 있었을 것이고 문제를 해결하기 위해 다른 라이브러리를 사용했을 것입니다. 그리고 Vue가 특정 문제를 더 잘 해결할 수 있는지 알고 싶기 때문에 이 것을 보고 있을 것입니다. 이것이 우리가 당신을 위해 말하고자하는 것입니다.

우리는 편견을 피하려고 아주 열심히 하고 있습니다. 코어 팀으로서 우리는 Vue를 좋아합니다. 우리는 우리가 더 잘 해결할 수 있다고 생각하는 몇 가지 문제가 있습니다. 이를 믿지 않는다면, 우리는 더 이상 연구하지 않을 것입니다. 우리는 공정하고 정확하기를 원합니다. React의 대체 렌더러에 대한 React의 광범위한 생태계 또는 Knockout의 IE6에 대한 브라우저 지원과 같은 다른 라이브러리가 중요한 이점을 제공하는 등이 우리가 다루려는 것 입니다.

자바 스크립트 세계가 빠르게 움직이기 때문에 이 문서를 최신 상태로 유지하는 **당신의** 도움을 받길 바랍니다. 정확하지 않다고 생각되는 부분이나 잘못된 부분이 있으면 [문제 제기](https://github.com/vuejs/vuejs.org/issues/new?title=Inaccuracy+in+comparisons+guide)로 알려주십시오.).

## React

React와 Vue는 많은 공통점을 공유합니다.

- 가상 DOM을 활용합니다.
- 반응적이고 조합 가능한 컴포넌트를 제공합니다.
- 코어 라이브러리에만 집중하고 있고 라우팅 및 전역 상태를 관리하는 컴패니언 라이브러리가 있습니다.

범위가 너무 비슷하기 때문에 이 비교를 다른 어떤 것보다 자세하게 보는데 더 많은 시간을 투자했습니다. 우리는 기술적 정확성뿐만 아니라 균형을 유지하기를 원합니다. React가 Vue보다 더 빛나는 곳, 예를 들어 생태계가 풍부하고 커스텀 렌더러가 풍부하다는 점을 지적합니다.

그렇다고해서 비교 대상이 일부 React 사용자에게 Vue에 편향된 것처럼 보이는 것은 피할 수 없는 사실입니다. 많은 주제가 탐구되는 것은 어느 정도 주관적입니다. 우리는 다양한 기술적 취향의 존재를 인정합니다. 이 비교는 당신의 취향이 우리와 맞을 경우 Vue가 잠재적으로 더 적합할 수 있는 이유를 개략적으로 설명하기 위한 것입니다.

React 팀의 Dan Abramov 덕분에 React 커뮤니티는 [이러한 균형을 이루는데 도움](https://github.com/vuejs/vuejs.org/issues/364)이 되었습니다. 그는 우리가 최종 결과에 대해 [모두 만족할 때까지](https://github.com/vuejs/vuejs.org/issues/364#issuecomment-244575740)이 문서를 수정하는 데 도움이되는 시간과 상당한 전문성을 지극히 관대했습니다.

Some of the sections below may also be slightly outdated due to recent updates in React 16+, and we are planning to work with the React community to revamp this section in the near future.

### 런타임 퍼포먼스

React와 Vue 모두 비슷하게 빠르므로 속도는 선택에 있어 결정적인 요인이 되지는 않을 것입니다. 특정 측정 항목에 대해서는 매우 간단한 컴포넌트 트리를 사용하여 원시 렌더링/업데이트 성능에 초점을 맞추는 [써드파티 벤치 마크](https://stefankrause.net/js-frameworks-benchmark8/table.html)를 확인하십시오.


#### 렌더링 성능

UI를 렌더링 할 때 일반적으로 DOM을 조작하는 것이 가장 비용이 많이 드는 작업이며 유감스럽게도 라이브러리는 이러한 원시 작업을 더 빠르게 만들 수 없습니다. 우리가 할 수 있는 최선의 방법은 다음과 같습니다.

1. 필요한 DOM 조작 수를 최소화합니다. React와 Vue는 모두 가상의 DOM 추상화를 사용하여 이 작업을 수행하며 두가지 구현 모두 거의 동일하게 작동합니다.

2. DOM 조작에 가능한 적은 오버헤드(순수 JavaScript 계산)만 가합니다. 이 것은 Vue와 React의 차이입니다.

JavaScript의 오버헤드는 필요한 DOM 작업을 계산하는 메커니즘과 직접적으로 관련이 있습니다. Vue와 React 모두 가상 DOM을 사용하여 이를 구현하지만 Vue의 가상 DOM 구현([snabbdom](https://github.com/snabbdom/snabbdom)의 포크)은 훨씬 가벼우므로 React보다 더 적은 오버 헤드가 발생합니다.

Vue와 React 모두 상태가 없고 및 인스턴스가 없는 컴포넌트를 제공하므로 오버 헤드가 적습니다. 이러한 성능이 중요한 상황에서 사용되면 Vue가 다시 한 번 더 빠릅니다. 이를 입증하기 위해 우리는 10,000 개의 목록 항목을 100 번 렌더링하는 간단한 [벤치 마크 프로젝트](https://github.com/chrisvfritz/vue-render-performance-comparisons)를 만들었습니다. 결과는 하드웨어와 사용되는 브라우저에 따라 다르므로 실제로 시도해 보는 것이 좋습니다. 실제로는 JavaScript 엔진의 특성으로 인해 실행간에 차이는 있습니다.

약간 귀찮더라도, 아래는 2014 년 MacBook Air의 Chrome 52에서 실행 된 숫자입니다. 체리 피킹을 피하기 위해 두 벤치 마크는 실제로 20번의 별도 시간에 실행되었으며 아래에 포함 된 최상의 실행 결과가 있습니다.

{% raw %}
<table class="benchmark-table">
  <thead>
    <tr>
      <th></th>
      <th>Vue</th>
      <th>React</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Fastest</th>
      <td>23ms</td>
      <td>63ms</td>
    </tr>
    <tr>
      <th>Median</th>
      <td>42ms</td>
      <td>81ms</td>
    </tr>
    <tr>
      <th>Average</th>
      <td>51ms</td>
      <td>94ms</td>
    </tr>
    <tr>
      <th>95th Perc.</th>
      <td>73ms</td>
      <td>164ms</td>
    </tr>
    <tr>
      <th>Slowest</th>
      <td>343ms</td>
      <td>453ms</td>
    </tr>
  </tbody>
</table>
{% endraw %}

#### 갱신 성능

React에서는 컴포넌트의 상태가 변경되면 해당 컴포넌트에서 루트로 시작하여 전체 컴포넌트 하위 트리를 다시 렌더링합니다. 불필요한 자식 컴포넌트의 재 렌더링을 피하려면 어디에서나 `shouldComponentUpdate`를 구현하고 변경 불가능한 데이터 구조를 사용해야 합니다. Vue에서 컴포넌트의 종속성은 렌더링 중 자동으로 추적되므로 시스템은 실제로 다시 렌더링해야하는 컴포넌트를 정확히 알고 있습니다.

즉 최적화되지 않은 Vue의 업데이트는 최적화되지 않은 React보다 훨씬 빠르며 실제로 Vue의 렌더링 성능이 향상되므로 완전히 최적화 된 React도 보통 Vue가 기본 제공되는 것보다 느립니다.

#### 개발에 있어서

프로덕션 환경에서의 성능은 최종 사용자 경험과 직접 관련되어 있기 때문에 더 중요한 부분이지만 개발 경험은 개발자 경험과 관련되어 있으므로 여전히 중요합니다.

Vue와 React 모두 거의 대부분의 일반적인 애플리케이션에서 속도가 빠릅니다. 그러나 높은 프레임 속도의 데이터 시각화 또는 애니메이션을 프로토 타이핑 할 때 Vue는 개발시 초당 10 프레임을 처리하는 반면 React는 초당 약 1 프레임으로 떨어지는 경우를 보았습니다.

이것은 많은 우수한 경고와 오류 메시지를 제공하는 데 도움이되는 개발 모드에서의 React의 많은 무질서한 검사 때문입니다. 우리는 이 것들이 Vue에서도 중요하다는 것에 동의하지만, 이를 이행하는 동안 성과를 면밀히 관찰하려고 노력했습니다.

### HTML & CSS

React에서는 모든 것이 JavaScript입니다. JSX를 통해서 HTML 구조가 들어와있을 뿐만 아니라 요즘에는 CSS 관리도 JavaScript에서 하는 추세죠. 이 접근 법도 나름대로 장점이 있습니다만 모든 개발자들에게 적합하다고 하기에는 단점이 좀 있습니다.

Vue는 고전적인 웹기술들을 받아들여서 그 기반 위에 만들어졌습니다. 몇 가지 예를 통해서 무슨 뜻인지 살펴보겠습니다.

#### JSX vs Template

React에서 모든 컴포넌트는 JSX를 사용하는 렌더링 함수를 통해서 UI를 표현합니다. JSX는 JavaScript에서 작동하는 선언적인 XML 유사 문법입니다.
React에서 모든 컴포넌트는 JavaScript에서 작동하는 선언적 XML 유사 구문인 JSX를 사용해 렌더링 함수 안에서 UI를 표현합니다.

JSX를 이용하는 렌더링 함수를 사용하면 몇 가지 장점이 있습니다.

- 완전한 프로그레밍 언어(JavaScript)를 이용해서 뷰를 만들 수 있습니다. 임시 변수, 플로우 제어에 스코프 내에서 직접적으로 JavaScript의 값을 가져다 쓸 수도 있겠죠.
- JSX의 툴 지원(예: linting, 형 검사, 자동완성 기능)은 어떤 측면에서 현재 사용할 수 있는 Vue 템플릿보다 더 진보된 기능입니다.

Vue에서도 [렌더링 함수](render-function.html)에 심지어 [JSX 지원](render-function.html#JSX)을 쓸 수 있습니다. 때로는 그 힘이 필요하거든요. 하지만 기본적으로는 템플릿 이용을 더 간단한 대안으로 제공합니다. 때로는 그 강력함이 필요하기 때문입니다. 그러나 기본적으로 우리는 더 간단한 대안으로 템플릿을 제공합니다. 잘 작동하는 HTML은 Vue 템플릿으로도 잘 작동하며 여기에서 오는 장점들이 있습니다.

- HTML로 작업해온 많은 개발자에게는 템플릿을 읽고 쓰는 것이 어렵지 않습니다. 선호라는 것은 다소 주관적일 수도 있겠지만 개발자의 생산성이 올라간다면 그건 객관적인 거죠.
- HTML 기반 템플릿을 이용하면 기존의 어플리케이션을 Vue로 점진적으로 이전하기가 훨씬 쉽습니다.
- 또한 디자이너와 경험이 적은 개발자들이 코드를 분석하고 기여하기에도 훨씬 쉽습니다.(역자: 러닝 커브가 낮습니다)
- Vue 템플릿을 쓸 때 Pug(이전의 Jade)같은 프리프로세서를 사용할 수도 있습니다.

어떤 사람들은 템플릿을 작성하기 위해서는 별도의 언어(DSL, Domain-Specific Language)를 또 배워야 한다고도 합니다. 하지만 저희가 볼 때는 그 차이가 기껏해봐야 매우 피상적인 수준이라고 생각합니다. 먼저 JSX도 사용하려면 학습을 해야 합니다. JSX도 플레인 JavaScript에 문법이 추가되어 있어서 JavaScript에 익숙한 사람이라면 공부할 것이 많지는 않겠지만 따로 더 배울게 없다고 할 수는 없죠. 비슷하게 템플릿도 플레인 HTML에 문법을 추가한 것이라서 HTML에 익숙한 사람에게는 공부할 것이 많지 않습니다. 별도의 언어(역자: 템플릿 문법)를 써서 사용자들이 더 적은 코드(예: `v-on` 수식어)를 써서 더 많을 것을 처리할 수 있습니다. JSX나 렌더링 함수를 쓰면 같은 일을 처리하기 위해서 더 많은 코드를 써야 합니다.

좀 더 높은 수준에서 이야기하자면 컴포넌트는 표현형과 논리형 두 가지로 나눌 수 있습니다. 템플릿은 표현형 컴포넌트에, 렌더링 함수와 JSX는 논리형 컴포넌트에 사용하는 것이 좋습니다. 어떤 어플리케이션을 만드는가에 따라 어느 형의 컴포넌트가 많을 지는 다릅니다만 일반적으로는 표현형 컴포넌트가 더 많습니다.

#### 컴포넌트 범위의 CSS

컴포넌트를 여러 파일 (예: [CSS 모듈](https://github.com/gajus/react-css-modules))을 통해 배포하지 않는 한 React의 CSS 범위 지정은 CSS-in-JS 방식으로 해결합니다. (e.g. [styled-components](https://github.com/styled-components/styled-components), [glamorous](https://github.com/paypal/glamorous), 그리고 [emotion](https://github.com/emotion-js/emotion)) 이는 일반적인 CSS 작성 프로세스와는 다른 새로운 컴포넌트 지향 스타일링 패러다임을 뜻합니다. 또한 빌드타임에 단일 스타일시트에 CSS를 추출할 수 있는 지원이 있지만 스타일이 제대로 작동하려면 런타임이 번들에 포함되어야하는 것이 일반적입니다. 스타일을 작성하는 동안 JavaScript의 역동적인 기능을 사용할 수 있지만 증가한 번들 크기 및 런타임 비용으로 종종 그 대가를 치룹니다.

CSS-in-JS의 팬이라면 유명한 CSS-in-JS 라이브러리들도 Vue를 지원한다는 점을 눈여겨봐주시기 바랍니다.(예 [styled-components-vue](https://github.com/styled-components/vue-styled-components)와 [vue-emotion](https://github.com/egoist/vue-emotion)). 여기서 React와 Vue의 가장 큰 차이점은 Vue에서는 기본 스타일링 방식으로 [싱글 파일 컴포넌트](single-file-components.html) 안에서 우리에게 익숙한 `style` 태그를 사용한다는 것입니다.

[싱글 파일 컴포넌트](single-file-components.html)를 통해서 다른 컴포넌트 코드와 마찬가지로 CSS에 접근할 수 있습니다.

``` html
<style scoped>
  @media (min-width: 250px) {
    .list-container:hover {
      background: orange;
    }
  }
</style>
```

옵션인 `scoped` 속성은 자동적으로 엘리먼트에 유일한 속성(예 : `data-v-21e5b78`)을 추가해서 `.list-container:hover`를 `.list-container[data-v-21e5b78]:hover`로 컴파일 합니다.

마지막으로 Vue의 싱글 파일 컴포넌트의 스타일은 매우 유연합니다. [vue-loader](https://github.com/vuejs/vue-loader)를 통해 전처리기, 포스트 프로세서 및 [CSS Modules](https://vue-loader.vuejs.org/en/features/css-modules.html)와의 긴밀한 통합을 할 수 있습니다.  모든 스타일은 `<style>` 엘리먼트 안에 있습니다.

### 규모

#### 규모 확장

대형 애플리케이션의 경우 Vue와 React는 강력한 라우팅 솔루션을 제공합니다. React 커뮤니티는 또한 상태 관리 솔루션 (Flux/Redux 등) 측면에서 매우 혁신적입니다. 이러한 상태 관리 패턴과 [심지어 Redux 자체](https://github.com/egoist/revue)는 Vue 애플리케이션에 쉽게 통합할 수 있습니다. 실제로, Vue는 우수한 모델 개발 경험을 제공한다고 생각하는 Vue에 깊이 통합되어있는 Elm의 영감을받은 상태 관리 솔루션인 [Vuex](https://github.com/vuejs/vuex)를 통해 이 모델을 더욱 발전 시켰습니다.

또 다른 중요한 차이점은 상태 관리 및 라우팅을 위한 Vue의 기타 라이브러리 ([기타 관심사](https://github.com/vuejs) 중)는 모두 공식적으로 지원되며 핵심 라이브러리와 함께 최신 상태로 유지된다는 것입니다. 반대로 React는 커뮤니티에 이러한 결정을 맡기고 더 분열 된 생태계를 만드는 것을 선택했습니다. 그 결과 React의 생태계는 Vue보다 훨씬 풍부합니다.

마지막으로, Vue는 [CLI 프로젝트 생성기](https://github.com/vuejs/vue-cli)를 제공하여, 대화형식의 프로젝트 구축마법사를 이용해 새로운 프로젝트를 간단하게 시작할 수 있습니다. 또한, 컴포넌트의 [인스턴트 프로토타이핑](https://cli.vuejs.org/guide/prototyping.html#instant-prototyping) 또한 사용할 수 있습니다. 리액트에도 [create-react-app](https://github.com/facebookincubator/create-react-app)이 있고, 이 분야에서 진보를 이루고 있습니다만, 현상황에서는 몇가지 제약이 있습니다.

- It does not allow any configuration during project generation, while Vue CLI runs on top of an upgradeable runtime dependency that can be extended via [plugins](https://cli.vuejs.org/guide/plugins-and-presets.html#plugins).
- 단일 페이지 애플리케이션을 작성한다고 가정하는 단일 템플릿만 제공하며, Vue는 다양한 목적을 위해 다양한 템플릿를 제공하고 시스템을 빌드합니다.
- 엔터프라이즈 환경에서 특히 유용하게 사용될 수 있는 사용자 정의 [프리셋](https://cli.vuejs.org/guide/plugins-and-presets.html#presets)으로부터의 프로젝트 생성을 할수 없습니다.

이러한 제한 사항 중 상당수는 create-react-app 팀이 의도적으로 설계한 것입니다. 예를 들어, 프로젝트의 요구가 매우 간단하고 빌드 프로세스를 사용자 정의하기 위해 "추출"할 필요가없는 한, 이를 종속으로 업데이트 할 수 있습니다. 여기에서 [다른 철학](https://github.com/facebookincubator/create-react-app#philosophy)에 대해 더 많이 읽을 수 있습니다.

#### 규모 축소

React는 가파른 학습 곡선으로 유명합니다. 실제로 시작하기 전에 JSX와 아마도 ES2015+에 대해 알아야합니다. 많은 예제가 React의 클래스 구문을 사용하기 때문입니다. Babel Standalone을 기술적으로 사용하여 브라우저에서 코드를 라이브 컴파일 할 수는 있지만 작성에 적합하지 않기 때문에 빌드 시스템에 대해서도 배워야합니다.

React와 동일하게, Vue는 스케일 업도 가능한 한편, jQuery처럼 스케일 다운하는것 또한 가능합니다. 맞습니다. 처음 시작하기 위해서, 단 1줄의 스크립트 태그를 삽입하는것 만으로 충분합니다.

``` html
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

Vue 코드를 작성하고 성능 문제에 대해 걱정할 필요없이 걱정하지 않고 최소화 버전을 배포 버전에 제공 할 수 있습니다.

Vue를 시작하기 위해 JSX, ES2015 또는 빌드 시스템에 대해 알 필요가 없으므로 일반적으로 개발자가 일상적인 애플리케이션을 빌드하는 데 필요한 충분한 지식을 얻기 위해 [가이드](./)를 읽는 데 하루가 걸리지 않습니다.

### 네이티브 렌더링

ReactNative를 사용하면 같은 React 컴포넌트 모델을 사용하여 iOS 및 Android 용 기본 렌더링 애플리케이션을 작성할 수 있습니다. 이것은 개발자로서 여러 플랫폼에서 에 대한 지식을 적용할 수 있다는 점에서 매우 좋습니다. Vue는 Vue를 JavaScript 런타임으로 사용하는 Alibaba Group에서 개발 한 크로스 플랫폼 UI인 [Weex](https://alibaba.github.io/weex/)와 공식 협업을 맺고 있습니다. 즉, Weex를 사용하면 같은 Vue 컴포넌트 문법을 사용하여 브라우저에서 렌더링할 수 있을 뿐만 아니라 iOS 및 Android에서도 렌더링 할 수있는 컴포넌트를 작성할 수 있습니다!

현재 Weex는 아직 개발 중이며 ReactNative만큼 성숙하고 전투적인 테스트를 거치지는 않았지만 개발은 세계 최대의 전자 상거래 비즈니스의 생산 요구에 의해 주도되고 있고 Vue 팀은 적극적으로 협력 할 것입니다. Weex 팀과 함께 Vue 개발자를위한 원활한 경험을 보장합니다.

[NativeScript](https://www.nativescript.org/)는 또 다른 대안입니다. [커뮤니티 주도 플러그인](https://github.com/rigor789/nativescript-vue)이 개발 중입니다.

### MobX

MobX는 React 커뮤니티에서 꽤 유명해졌고 실제로 Vue와 거의 같은 반응형 시스템을 사용합니다. 제한된 범위 내에서 React + MobX 워크플로우는 좀 더 장황한 Vue로 생각할 수 있습니다. 따라서 이 조합을 사용하고 있고 그것을 즐기고 있다면 Vue로 넘어오는 것이 아마도 다음 단계일 것입니다.

### Preact와 React 계열 라이브러리

React같은 라이브러리는 대개 실현 가능한 React와 API와 생태계를 공유하려고 노력합니다. 이러한 이유로, 위의 대부분의 비교도 그들에게 적용될 것입니다. 주된 차이점은 일반적으로 React에 비해 생태계가 현저히 축소되는 것입니다. 이러한 라이브러리들은 React 생태계의 모든 것과 100% 호환될 수 없으므로 일부 툴링 및 동반 라이브러리는 사용할 수 없을 수도 있습니다. 혹은 작동하는 것처럼 보여도, 당신 react계열 라이브러리가 React와 동등한 공식 지원을 받지 않는 한 언제라도 구현이 깨질 수도 있습니다.

### Preact and Other React-Like Libraries

React-like libraries usually try to share as much of their API and ecosystem with React as is feasible. For that reason, the vast majority of comparisons above will also apply to them. The main difference will typically be a reduced ecosystem, often significantly, compared to React. Since these libraries cannot be 100% compatible with everything in the React ecosystem, some tooling and companion libraries may not be usable. Or, even if they appear to work, they could break at any time unless your specific React-like library is officially supported on par with React.

## AngularJS (Angular 1)

일부 Vue의 문법은 Angular와 매우 유사합니다 (예 :`v-if`와`ng-if`). Angular가 제대로 된 많은 것들을 가지고 있었기 때문에 이것은 개발 초기에 Vue에게 영감이 되었습니다. Angular와 함께 제공되는 많은 고통이 있었지만 Vue가 상당한 개선을 제공하려고 시도하였습니다.

### 복잡도

Vue는 API와 디자인면에서 Angular 1보다 훨씬 간단합니다. 평범하지 않은 애플리케이션을 작성하기에 충분한 학습기간은 일반적으로 1 일 미만으로 소요되며 Angular 1에서는 그렇지 않습니다.

### 유연성과 모듈성

Angular는 애플리케이션을 어떻게 구성해야 하는지에 대한 강요가 강하고 Vue는 더욱 유연하고 모듈방식의 솔루션입니다. 이로 인해 Vue는 다양한 프로젝트에보다 적합하게 적용될 수 있으며, 때로는 코딩을 시작하기 위해 의사 결정을 내리는데 유용 할 때가 있습니다.

그렇기 때문에 핫 모듈 리로딩, 린트 (linting), CSS 추출과 같은 고급 기능에 대한 액세스 권한을 부여하는 동시에 빠르게 설정할 수있는 [Vue CLI](https://github.com/vuejs/vue-cli)를 제공합니다.

### 데이터 바인딩

Angular 1은 스코프간 양방향 바인딩을 사용하는 반면 Vue는 컴포넌트 간에 단방향의 데이터 흐름을 사용합니다. 이로 인해 데이터의 흐름이 단순한 애플리케이션에서는 데이터의 흐름을 쉽게 파악할 수 있습니다.

### 디렉티브 vs 컴포넌트

Vue는 디렉티브와 컴포넌트를 명확하게 구분합니다. 지시어는 DOM 조작만 캡슐화 하기 위한 것이고 컴포넌트는 자체 뷰와 데이터 로직이 있는 자체의 포함 단위입니다. Angular에서는 이 둘 사이에 많은 혼란이 있습니다.

### 런타임 퍼포먼스

Vue는 더 나은 성능을 가지며 변경에 대한 검사를 하지 않기 때문에 훨씬 쉽게 최적화 할 수 있습니다. Angular 1은 감시자가 많으면 느려집니다. 범위가 변경 될 때마다 이러한 모든 감시자를 다시 평가해야하기 때문입니다. 또한 일부 감시자가 다른 업데이트를 트리거하는 경우 다이제스트 주기를 여러 번 실행하여 "안정화"해야 할 수도 있습니다. Angular 사용자는 다이제스트 주기를 벗어나기 위해 종종 숨겨진 기술에 의지해야하며 경우에 따라 많은 감시자와 함께 범위를 최적화 할 수있는 방법이 없습니다.

Vue는 비동기 대기열이 있는 투명한 종속성 추적 관찰 시스템을 사용하기 때문에이 문제가 전혀 발생하지 않습니다. 모든 변경 사항은 명시적 종속 관계가 없는 한 독립적으로 트리거됩니다.

흥미롭게도 AngularJS와 Vue가  문제를 해결하는 방법에는 몇 가지 유사점이 있습니다.

## Angular (Formerly known as Angular 2)

Angular 2는 완전히 새로운 것이기 때문에 별도의 섹션을 만들었습니다. 예를 들어, 1급 컴포넌트 시스템이 있으며 많은 구현 세부 사항이 완전히 다시 작성 되었으며 API도 상당히 크게 변경되었습니다.

### TypeScript

Angular는 TypeScript가 필수적입니다. 문서 또한 TypeScript 기반입니다. TypeScript를 사용하면 Java와 C#을 다루던 사용자에게 생산성을 올려주고 정적 타입 체크 등의 많은 이익이 있습니다. 그러나 모든 사람들이 TypeScript를 사용하려고 하지는 않습니다.

많은 소규모 사례에서 TypeScript를 사용하면 생산성 향상보다 더 많은 오버헤드가 발생할 수 있습니다. 이 경우 TypeScript 없이 Angular를 사용하는 것이 어려울 수 있기 때문에 Vue를 사용하는 것이 좋습니다.

Vue는 [엔터프라이즈 환경](https://github.com/vuejs/awesome-vue#enterprise-usage)에도 매우 적합하며 [공식 Typings](https://github.com/vuejs/vue/tree/dev/types) 및 [공식 decorator](https://github.com/vuejs/vue-class-component)를 통해 TypeScript와 함께 사용할 수도 있습니다.

### 런타임 퍼포먼스

두 프레임워크 모두 빠르며 비슷한 벤치마크 결과를 보여줍니다. [브라우저에 초점을 맞춘 분석](http://www.stefankrause.net/js-frameworks-benchmark7/table.html)을 보면 더욱 상세하게 비교를 하실 수 있을 것입니다. 그러나 속도는 선택할 때 큰 영향을 줄 것으로 생각되지 않습니다.

### 용량

최신 [AOT compilation](https://en.wikipedia.org/wiki/Ahead-of-time_compilation)과 [tree-shaking](https://en.wikipedia.org/wiki/Tree_shaking)을 포함한 Angular는 크기가 매우 작어졌습니다. 그럼에도 불구하고 모든 기능을 갖춘 Vue 2 프로젝트(~30kb gzipped)는 `angular-cli`(~130kb gzipped)보다 훨씬 작습니다.

### 유연성

Vue는 Angular 2보다 훨씬 덜 강요적이며, 다양한 빌드 시스템에 대한 공식적인 지원을 제공하며 애플리케이션 구조를 제한하지 않습니다. 많은 개발자가 이러한 자유를 누리고 있지만 일부 개발자는 모든 애플리케이션을 빌드하는 데 올바른 방법이 하나만 있는 것을 선호합니다.

### 학습 곡선

Vue를 시작하려면 HTML 및 ES5 JavaScript (즉, 일반 자바 스크립트)에 익숙해야합니다. 이러한 기본 기술을 사용하면 [안내서](./)를 읽는 하루 만에 작은 애플리케이션을 작성할 수 있습니다.

Angular의 학습곡선은 훨씬 가파릅니다. 프레임워크 API는 방대하며 생산성이 올라가기 전에 매우 많은 것들을 알아야합니다. Angular의 복잡성은 대규모 앱을 목표로 합니다. 하지만 경험이 부족한 개발자가 선택하기에 훨씬 어렵습니다.

## Ember

Ember는 높은 찬사를 받는 완전한 기능의 프레임워크입니다. 그것은 많은 기존의 관행을 제공하며, 일단 익숙해지면 생산성을 높일 수 있습니다. 그러나 이는 학습 곡선이 높고 유연성이 떨어지는 것을 의미합니다. 함께 작동하는 느슨하게 결합 된 도구 집합을 사용하여 독창적인 프레임워크와 라이브러리를 선택하려고 하면 트레이드 오프가 있습니다. 후자는 더 많은 자유를 제공하지만 더 많은 구조에 대한 결정을 요구합니다.

즉, Vue 코어와 Ember의 [templating](https://guides.emberjs.com/v2.10.0/templates/handlebars-basics/) 및 [객체 모델](https://guides.emberjs.com/v2.10.0/object-model/) 레이어을 비교하면 더 잘 알 수 있습니다.

- Vue는 일반 JavaScript 객체 및 완전히 자동으로 계산된 속성에 대해 눈에 거슬리지 않는 반응형을 제공합니다. Ember에서는 Ember 객체의 모든 것을 랩핑하고 계산된 속성의 종속성을 수동으로 선언 해야합니다.

- Vue의 템플릿 문법은 JavaScript 표현식의 모든 기능을 활용하지만 Handlebars의 표현식 및 헬퍼 문법은 의도적으로 비교할 때 매우 제한적입니다.

- 성능 측면에서 Vue는 Ember 2.0의 최신 Glimmer 엔진 업데이트 이후에도 Ember보다 [월등히](http://www.stefankrause.net/js-frameworks-benchmark7/table.html) 뛰어납니다. Vue는 업데이트를 자동으로 일괄 처리하지만 Ember에서는 성능이 중요한 상황에서 실행 루프를 수동으로 관리해야합니다.

## Knockout

Knockout은 MVVM 및 의존성 추적의 개척자였으며 반응형 시스템은 Vue의 그것과 매우 유사합니다. [브라우저 지원](http://knockoutjs.com/documentation/browser-support.html)은 IE6에 대한 지원과 함께 모든 것을 고려하여 매우 인상적입니다! Vue는 IE9+ 만 지원합니다.

하지만 시간이 지남에 따라 개발 속도가 느려졌고 오래되어 보이기 시작했습니다. 예를 들어 컴포넌트 시스템에는 라이프 사이클 훅이 전혀 없으며 매우 일반적인 사용 사례이지만 컴포넌트에 자식을 전달하기위한 인터페이스는 [Vue](components.html#Content-Distribution-with-Slots)에 비해 약간 어색함을 느낄 수 있습니다.

API 디자인에는 철학적인 차이가 있는 것 같아 호기심이 생긴다면 [단순한 할 일 목록](https://gist.github.com/chrisvfritz/9e5f2d6826af00fcbace7be8f6dccb89)을 어떻게 작성하는지 보여줄 수 있습니다. 분명히 다소 주관적이지만, 많은 사람들은 Vue의 API가 덜 복잡하고 구조가 잘 구성되어 있다고 생각합니다.

## Polymer

Polymer는 Google이 후원하는 또 다른 프로젝트이며 실제로 Vue의 영감의 원천이었습니다. Vue의 컴포넌트는 Polymer의 사용자 지정 엘리먼트와 느슨하게 비교할 수 있으며 둘 다 매우 유사한 개발 스타일을 제공합니다. 가장 큰 차이점은 Polymer는 최신 웹 컴포넌트 기능을 기반으로하며 이러한 기능을 기본적으로 지원하지 않는 브라우저에서는 성능이 저하되는 약간의 폴리필을 요구합니다. 대조적으로, Vue는 IE9에 의존성이나 폴리필이 없이도 작동합니다.

Polymer 1.0에서 팀은 성능을 보완하기 위해 데이터 바인딩 시스템을 매우 제한적으로 만들었습니다. 예를 들어, Polymer 템플릿에서 지원되는 유일한 표현식은 Boolean 부정 및 단일 메소드 호출입니다. 계산된 속성 구현 또한 매우 유연하지 않습니다.

Polymer 사용자 정의 엘리먼트는 HTML 파일로 제작되어 일반 JavaScript/CSS(및 현재 브라우저에서 지원되는 언어 기능)로 제한됩니다. 이에 비해 Vue의 싱글 파일 컴포넌트를 사용하면 ES2015+ 및 원하는 모든 CSS 전처리기를 쉽게 사용할 수 있습니다.

프로덕션 환경으로 배포 할 때 Polymer는 브라우저에서 스펙을 구현한다고 가정하는 HTML 가져오기 및 서버와 클라이언트 모두에서 HTTP/2 지원을 사용하여 모든 것을 로드하는 것을 권장합니다. 이는 대상 사용자 및 배포 환경에 따라 가능할 수도 있고 그렇지 않을 수도 있습니다. 이것이 바람직하지 않은 경우에는 Vulcanizer라고하는 특수 도구를 사용하여 폴리머 엘리먼트를 묶어야합니다. 앞에서 볼 때 Vue는 비동기 컴포넌트 기능과 Webpack의 코드 분할 기능을 결합하여 애플리케이션 번들의 일부를 지연 로드 되도록 쉽게 분리 할 수 있습니다. 이를 통해 이전 브라우저와의 호환성을 유지하면서 앱 로드 성능을 높일 수 있습니다.

Vue와 사용자 정의 엘리먼트 및 Shadow DOM 스타일 캡슐화와 같은 웹 컴포넌트 스펙을 더욱 완벽하게 통합하는 것도 가능합니다. 그러나 현재로서는 모든 주요 브라우저에서 사양을 성숙시키고 광범위하게 구현하기를 기다리고 있습니다.

## Riot

Riot 3.0은 작고 아름답게 디자인 된 API를 사용하여 유사한 컴포넌트 기반 개발 모델 (Riot에서 "태그"라고 함)을 제공합니다. Riot과 Vue는 디자인 철학에 많은 부분을 공유합니다. 그러나 Vue는 Riot보다 약간 무겁지만 몇 가지 중요한 이점을 제공합니다.

- 더 나은 성능. 가상 DOM을 사용하는 것보다 Riot은 [DOM 트리 순회](http://riotjs.com/compare/#virtual-dom-vs-expressions-binding)를 하므로 앵귤러 1과 같은 성능 문제가 있습니다.
- 보다 성숙한 도구 지원. Vue는 [Webpack](https://github.com/vuejs/vue-loader)및 [Browserify](https://github.com/vuejs/vueify)에 대한 공식적으로 지원하지만 Riot는 빌드 시스템 통합을 커뮤니티 지원에 의존합니다.
