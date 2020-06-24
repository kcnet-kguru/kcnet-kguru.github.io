---
layout: post
title:  "[KGURU] 나만의 TODO App 만들기 - Front End 와 Back End"
author: "장상익"
comments: true
---
### KURU 나만의 TODO App 만들기 - Front End 와 Back End

안녕하세요 KGuru 장상익 입니다. 

이번 ToDo List App 에서는 Front End - Back End - DataBase 형태의 3 tier archtecture를 사용하였습니다.<br>
일반적인 JAVA/jsp에서 presentation layer를 Front 라고 생각하시는 분들이 많은 듯 하지만, 사실 제가 생각하는 Front End는 많이 다릅니다.

아래 그림이 JAVA/jsp 에서 많이 사용하는 고전적 아키텍쳐입니다.

<img src="/assets/images/todolist/old-3tier.png" width="50%" height="30%" title="고전적인 3 티어" alt="old-3tier">

그림에서 보다 시피 WAS에 presentation layer 가 WEB 과 강하게 결합이 되어 있습니다. 만약 WAS가 멈추면, 동적 html 을 전달하지 못하여 WEB에서는 static resource (css, js, imgaes)<br/>
만을 전달하므로 브라우저에는 아무런 화면도 표시할 수 없거나 WEB에 설정되어 있는 404, 500 에러 페이지가 표시 될 것입니다. 즉, 웹 서비스의 중단된 모습을 사용자에게 노출 되어 집니다. <br/>
아마 사용자들이 서비스가 멈춘 사이트는 두 번 다시 찾고 싶은 생각이 들지 않을 거 같습니다.

또한, 모든 html은 WAS에서 파싱해서 WEB에 제공하므로, 트래픽에 따른 부하를 WEB을 거쳐 WAS까지 영향을 받게 됩니다. 물론 WEB을 분리하여 static resource에 대한 부하는 줄였지만, 여전히 WAS는 피곤합니다. 

그리고 개발자가 집중할 수 있는 영역 또한 명확하지 않은 형태 였습니다. java 웹 개발자가 javascript도 필수로 알아야하고 css도 어느정도 이해해야 하며, Front 와 Back을 동시에 처리하여야 하는 역할을 
동시에 수행해야 하기 떄문에, 개발자의 정체성 또한 모호했습니다. 아직까지 현재 java 웹개발자가 Front 개발자라고 생각하시는 분들도 많은 듯합니다. jsp 특성상 java 코드를 html과 같이 사용하기 떄문에 
DOM을 제어하는 부분정도를 javascript를 학습하여 아는 것 정도 일뿐,  javascript의 깊은 부분까지는 잘 알지 못하는 경우가 많습니다.(모두가 그렇진 않겠지만, 제가 만난 개발자들은 대개 그랬던거 같습니다.)

최근까지 여러 연구와 시도 끝에 여러가지 아키텍처가 구상, 구현되었고, B2C 회사들은 진화하는 소프트웨어를 위해 고전적인 아키텍쳐보다 진화한 아키텍처를 선택하여 사용하고 있습니다.
아래와 같은 형태가 이번 Todolist Application에서 선택한 아키텍쳐 입니다.

<img src="/assets/images/todolist/now-3tier.png" width="50%" height="30%" title="고전적인 3 티어" alt="old-3tier">

고전적인 아키텍처와 똑같이 3tier Achitecture 이지만, 이 아키텍처는 정확히 WEB 과 WAS의 역할이 주어져 있습니다. 
WEB은 사용자와의 인터페이스를 담당하고 있고, WAS는 WEB에서 요청하는 Data 전달에 대한 부분만 담당하게 되는 형태로 변화하게 되었습니다.
즉, WEB은 기존에 WAS에 의존적인 부분을 분리하여 WEB 만의 아키텍쳐를 가지고, 독립적으로 구성이 될 수 있으며, WAS 또한 WEB에 영향을 주지 않고 독립적인 아키텍쳐로 구성할 수 있는 아키텍쳐입니다.

WEB은 기존에 static resource 뿐만 아니라 동적 html 구성이 가능하게 되어  WAS와 무관하게 동작하면서, 필요할 때만 데이터베이스 데이터를 관리하거나 WAS에 필요한 비즈니스 로직을 실행합니다. 이 때 WAS 와 인터페이스 하는 방식이 REST-API를 활용하여, 인터페이스 하게 됩니다. 

그래서 WEB에서 동작하는 시스템의 아키텍쳐를 담당하는 Front End Engineer(이후 FEE)가 생겨나게 되었고, FEE 는 기존의 아키텍트와 같이 WEB영역의 아키텍트 역량을 가지고 있어야 합니다. 그러기 위해선 브라우저, css, js, html 등 깊은 이해가 필요합니다. 여기에 약간의 디자인 역량까지 더해지면 금상첨화 입니다. 그래서 예전 웹디자인과 퍼블리싱을 했던 개발자 들이 학습을 통해 FEE로 전직하는 추세 입니다.

### Front End Web Library & Framework

현재 Front End Web App을 구현하는 데 있어 대표적으로 사용하는 프레임워크나 라일브러리로는 Angular, React, Vue.js 세가지를 손에 꼽을 수 있을 것입니다.(라이브러리라고 표현한 이유는 React는 라이브러리이기 때문입니다.)

아래 이미지는 Github star 수 변화 그래프 입니다.
<img src="/assets/images/todolist/star-history.PNG" width="80%" height="80%" title="비교" alt="star-history">

압도적으로 React와 Vue 가 Anglar에 비해 높은 star 수를 받고 있으며, 최근에는 Vue 가 더 높은 star수를 기록한 것을 볼 수 있습니다.
start수가 많다고 좋은 것은 아니지만, 개발자들이 직접 사용해본 경험을 토대로 star를 부여하기에 의미가 있습니다.

React 보다 Vue 가 최근 들어 더 많은 star를 받게 된 것은 학습 곡선 때문입니다. React는 모두 javascript로 되어 있어서 학습 난이도가 높습니다. 
하지만 그만큼 더 많은 것을 확장해서 사용할 수 있는 유연함을 지니고 있고, 여러 업무 분야에서 사용할 수 있는 장점이 있습니다.(React Native는 React기반으로 모바일 앱을 구현할 수 있게 해주기도 합니다.)

Vue 는 html 과 javascript, css를 혼용하여 템플릿 형태로 프레임워크를 제공해 줍니다. 물론 React와 같이 라이브러리로 사용할 수 있지만, 프레임워크가 제공하는 기능에는 많이 못미치는 수준입니다.
기존에 익숙한 html과 js, css를 활요하기 때문에 React 보다는 학습 곡선이 낮아 배우기 쉽습니다. 그렇다고 아예 학습이 불필요하진 않습니다. 
하지만, Vue 는 큰 Enterpise 같은 무겁고 복잡한 시스템에는 적용하기 쉽지 않다는 단점을 지니고 있습니다. 그래서 Vue.js 로 구현되는 시스템들은 어느정도 단순하고 가벼운 시스템에 많이 사용되고 있습니다.

여러가지를 고려해본 결과 React처럼 학습난이도가 높은 것 보단 이번 스터디에는 빠르게 익히고 사용할 수 있는 Vue.js를 사용하게 되었습니다.