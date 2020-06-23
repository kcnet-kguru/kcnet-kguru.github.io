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

<img src="/assets/images/todolist/old-3tier.png" width="40%" height="30%" title="고전적인 3 티어" alt="old-3tier"></img>

그림에서 보다 시피 WAS에 presentation layer 가 WEB 과 강하게 결합이 되어 있습니다. 만약 WAS가 멈추면, 동적 html 을 전달하지 못하여 WEB에서는 static resource (css, js, imgaes)<br/>
만을 전달하므로 브라우저에는 아무런 화면도 표시할 수 없거나 WEB에 설정되어 있는 404, 500 에러 페이지가 표시 될 것입니다. 즉, 웹 서비스의 중단된 모습을 사용자에게 노출 되어 집니다. <br/>
아마 사용자들이 서비스가 멈춘 사이트는 두 번 다시 찾고 싶은 생각이 들지 않을 거 같습니다.

또한, 모든 html은 WAS에서 파싱해서 WEB에 제공하므로, 트래픽에 따른 부하를 WEB을 거쳐 WAS까지 영향을 받게 됩니다. 물론 WEB을 분리하여 static resource에 대한 부하는 줄였지만, 여전히 WAS는 피곤합니다. 

그리고 개발자가 집중할 수 있는 영역 또한 명확하지 않은 형태 였습니다. java 웹 개발자가 javascript도 필수로 알아야하고 css도 어느정도 이해해야 하며, Front 와 Back을 동시에 처리하여야 하는 역할을 
동시에 수행해야 하기 떄문에, 개발자의 정체성 또한 모호했습니다. 아직까지 현재 java 웹개발자가 Front 개발자라고 생각하시는 분들도 많은 듯합니다. jsp 특성상 java 코드를 html과 같이 사용하기 떄문에 
DOM을 제어하는 부분정도를 javascript를 학습하여 아는 것 정도 일뿐,  javascript의 깊은 부분까지는 잘 알지 못하는 경우가 많습니다.(모두가 그렇진 않겠지만, 제가 만난 개발자들은 대개 그랬던거 같습니다.)

최근까지 여러 연구와 시도 끝에 여러가지 아키텍처가 구상, 구현되었고, B2C 회사들은 진화하는 소프트웨어를 위해 고전적인 아키텍쳐보다 진화한 아키텍처를 선택하여 사용하고 있습니다.
아래와 같은 형태가 이번 Todolist Application에서 선택한 아키텍쳐 입니다.

<img src="/assets/images/todolist/now-3tier.png" width="40%" height="30%" title="고전적인 3 티어" alt="old-3tier"></img>

고전적인 아키텍처와 똑같이 3tier Achitecture 이지만, 이 아키텍처는 정확히 WEB 과 WAS의 역할이 주어져 있습니다. 
WEB은 사용자와의 인터페이스를 담당하고 있고, WAS는 WEB에서 요청하는 Data 전달에 대한 부분만 담당하게 되는 형태로 변화하게 되었습니다.