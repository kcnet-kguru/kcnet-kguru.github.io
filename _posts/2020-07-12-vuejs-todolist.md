---
layout: post
title:  "[K-GURU] 나만의 TODO App 만들기 -Vue.js"
author: "장상익"
comments: true
---

### K-GURU 나만의 TODO App 만들기 - Vue.js

안녕하세요 K-GURU 장상익 입니다.<br/>

이번 포스트는 '나만의 Todo List 만들기'에서 Front End 부분을 담당했던 Vue.js에 대해서 다뤄보겠습니다.<br/>
현재 Web Front의 가장 인기 있는 라이브러리 혹은 프레임워크를 꼽으라 하면은 두말 할 것없이 'React', 'Angular', 그리고 'Vue.js' 입니다.

<img src="/assets/images/todolist/Lovedframeworks.png" width="50%" height="30%" title="Stackoverflow 설문조사" alt="Stackoverflow 설문조사">
위 이미지에서 확인 할 수 있다 시피 'React'와 'Vue'의 인기는 나날이 상승하고 있습니다.

소프트웨어 개발 생태계에서 꼭 어느 것이 좋다 라고 단정지을 수는 없습니다. 때와 상황에 맞춰 가장 적절한 선택을 하는 것이 최선이라고 생각합니다.<br/>

이번 K-GURU '나만의 Todo List 만들기'에서 'Vue.js'를 선택한 이유는 개인적으로 'React' 보다 학습곡선이 완만하고, 웹 개발자들에게 친숙한 html, javascript, css을 중심으로 프레임워크를 제공해주고 있다는 것이 선택의 이유입니다. 또한 생산성 측면에서도 jQuery 보다도 훨씬 높은 생산성을 보유하는 장점 또한 가지고 있습니다.
'Angular'는 구글 개발 되었고, 'React'는 Facebook에서, 'Vue'는 에반 유라는 개발자가 개발 하였습니다.

### Vue.js

Vue.js는 다음과 같은 특징이 있습니다.

<img src="/assets/images/todolist/Vuejs.png" width="70%" height="70%" title="Vuejs" alt="Vue.js">


### MVVM 패턴

Vue.js는 MVVM 패턴을 사용합니다. 먼저 많이 알려진 MVC 패턴에 대해 알아보겠습니다..<br/>

#### MVC 패턴

<img src="/assets/images/todolist/mvc.png" width="50%" height="30%" title="MVC 패턴" alt="MVC 패턴">

> 구조
> - Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분입니다.
> - View: 사용자에게 보여지는 UI 부분입니다.
> - Controller: 사용자의 입력(Action)을 받고 처리하는 부분입니다.

> 특징
> Conroller는 여러개의 View를 선택할 수 있는 1:n 구조입니다.
> Controller는 View를 선택할 뿐 직접 업데이트 하지 않습니다.

> 장점
> MVC 패턴의 장점은 단순하다는 것입니다.
> 단점
> MVC 패턴의 단점은 Vuew와 Model 사이의 의존성이 높다는 것입니다. View와 Model의 높은 의존성은 어플리케이션이 커질수록 복잡해지고 유지보수가 어렵게 만들 수 있습니다.

#### MVVM 패턴

<img src="/assets/images/todolist/mvc.png" width="50%" height="30%" title="MVC 패턴" alt="MVC 패턴">

> 구조
> - Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분입니다.
> - View: 사용자에게 보여지는 UI 부분입니다.
> - ViewModel: View를 표현하기 위해 만든 View를 위한 Model입니다. View를 나타내 주기 위한 Model이자 View를 나타내기 위한 데이터를 처리하는 부분입니다.

> 특징
> MVVM 패턴은 Command 패턴과 Data Binding 두 가지 패턴을 사용하여 구현되었습니다.
> Command 패턴과 Data Binding을 이용하여 View와 View Model 사이의 의존성을 없앴습니다.
> View Model과 View는 1:n 관계입니다.

> 장점
> MVVM 패턴은 View와 Model 사이의 의존성이 없습니다. 또한 Command 패턴과 Data Binding을 사용하여 View와 View Model 사이의 의존성 또한 없앤 디자인패턴입니다. 각각의 부분은 독립적이기 때문에 모듈화 하여 개발할 수 있습니다.
> 단점
> MVVM 패턴의 단점은 View Model의 설계가 쉽지 않다는 점입니다.

### jQuery vs Vue.js

jQuery와 Vue.js의 차이점 중 가장 큰 부분은 elements에 대한 event 를 바인딩 하는 부분입니다.

<img src="/assets/images/todolist/jquery.png" width="70%" height="70%" title="jquery 이벤트 바인딩" alt="Stackoverflow jquery 이벤트 바인딩">

<img src="/assets/images/todolist/vue_event.png" width="70%" height="70%" title="vuejs 이벤트 바인딩" alt="Stackoverflow vuejs 이벤트 바인딩">

현재 국내에는 jQuery를 이용한 웹 시스템들이 많이 구축되어 있습니다. 하지만 최근 웹 개발 트렌드로 보면은 복잡한 jQuery 보다 더 간단 명료한 부분이 필요하다고 생각되는 듯 합니다. 그렇다고 jQuery가 성능적으로 좋은 라이브러리라고 얘기할 수 없을 듯 합니다..<br/>

시스템은 앞으로 점점 더 작은 단위로 나눠져서 개발자들이 본인들이 전문적으로 잘 할 수 있는 부분에 집중하도록 진화해 가고 있습니다. 그러한 과정에서 jQuery 보다는 다른 대안을 사용하는 움직일을 갖게 될 듯 합니다.

### 우리는 Vue.js를 쓸 수 있을까

아마 Vue.js라는 기술 보다 '공공기관 SI 프로젝트가 대부분인 회사에서 사용할 수 있을 것인가' 하는 질문에 대한 대답이 선행되어야 한다는 것이 필요할 것입니다.<br/>
사기업 SI 프로젝트에는 Vue.js나 React.js의 역량을 보유하는 사람들을 찾고 있는 구인공고가 조금씩 늘고 있는 추세입니다.
B2C 기업이나 스타트업에서는 벌써 채택하여 많은 기술 스택을 보유하고 있는 중입니다.
공공에서는 전자정부프레임워크 사용을 권고하고 있지만, 전자정부와 Vue는 엄연히 다른 부분입니다. <br/>

Vue.js를 사용한다는 것은 '전자정부프레임워크를 사용하지 않는다'는 것이 아니라, 'jsp 를 사용하지 않는다' 입니다.
Front End는 'Vue.js'를 사용하고, Back End로 '전자정부프레임워크'를 사용하면 된다고 생각합니다. '전자정부프레임워크' 적용 기준에 'jsp 를 필수로 해야 한다'는 부분은 보지 못했습니다.<br/>

어차피 시스템은 WEB-WAS-DB 3티어이고, 이 중에 WAS에서 처리 되던 부분을 WEB에 부하를 덜어주는 역할을 할 뿐 시스템의 전체 아키텍쳐도 달라질 이유가 없습니다.<br/>

그러므로 저는 '공공기관 SI에 적용 가능하다' 라고 생각합니다.


### Vue.js 학습 가이드

[Vue.js 공식 홈페이지(한국어)](https://kr.vuejs.org/) 에 가면 Vue.js에 대한 설명과 가이드를 확인 할 수 있습니다.
관심이 있으신 분은 해당 사이트를 통해 Vue.js에 대해서 학습 하실 수 있습니다.<br/>

Vue.js에 대한 질문이나 학습에 대해서 도움이 필요하시면 댓글로 질문을 남겨주시거나 저에게 메일을 보내주시면 최선을 다해 답변 드리겠습니다. 

## *K-GURU 는 지식을 공유하고 새로운 기술을 학습하는 모임입니다. 지식을 공유하고자 하시거나 새로운 기술을 같이 학습하고자 하시는 분들이 있으시다면, K-GURU에 참여 부탁드립니다.