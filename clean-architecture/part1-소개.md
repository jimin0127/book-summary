# 1부. 소개
## 1장. 설계와 아키텍처란?
- '아키텍처'는 고수준의 무언가를 가르킬 때 사용
- '설계'는 저수준의 구조 또는 결정사항 등을 의미할 때 사용
- 하지만 아키텍트가 하는 일을 살펴보면 둘 사이를 구분 짓기가 어렵다. 
- 저수준의 세부사항과 고수준의 구조는 모두 소프트웨어 전체 설계의 구성요소다.
- 둘은 개별로 존재할 수 없고 구분 짓는 경계가 뚜렷하지 않으며 이를 통해 대상 시스템의 구조를 정의한다. 
- 고수준에서 저수준으로 향하는 의사결정의 연속성만이 있을 뿐이다. 

### (좋은 소프트웨어 설계의) 목표는?
- 소프트웨어 아키텍처의 목표는 필요한 시스템을 만들고 유지보수하는데 투입되는 인력을 최소화하는데 있다. 
- 시스템의 수명이 다할 때까지 낮게 유지할 수 있다면 좋은 설계라고 말할 수 있다. 
- 새로운 기능을 출시할 때마다 비용이 증가한다면 나쁜 설계다. 

### 사례 연구
- 매번 새로운 기능을 출시할 때마다 개발자의 수는 지속적으로 증가했지만, 코드 생산성은 감소한다. 
- 코드 한 란인당 비용도 출시 기능에 따라 크게 증가한다. 
- 이런 비용 곡선은 사업 모델의 수익을 엄청나게 고갈 시키며, 회사의 성장을 멈추게 한다. 
#### 엉망진창이 되어 가는 신호
- 개발자의 생산성은 거의 100%로 시작했지만 출시할 때마다 하락한다. 
- 코드와 설계의 구조를 깔끔하게 만들려는 생각을 전혀하지 않으면 비용곡선은 크게 올라간다. 
- 개발자의 노력은 기능 개발보다는 엉망이 된 상황에 대처하는 데 소모되기 시작한다. 
- 사소한 기능이라도 엉망이 된 코드를 이동하는 반복 작업으로 변질된다. 
#### 경영자의 시각
- 인건비가 기능이 추가됨에 따라 계속 증가하는 추세다. 
- 하지만 많은 비용을 투자했지만 코드 라인과 생산성은 증가하지 않았다. 
#### 무엇이 잘못되었나?
- 토끼와 거북이 우화처럼 지나친 과신이 가진 어리석음이 문제다. 
- 개발자는 코드는 나중에 정리하고 당장 시장에 출시해야하는 것이 먼저라고 믿으며 결국 이전에 작성한 코드로 돌아가 정리하는 일은 하지 않는다. 
- 이는 다음 기능이 기다리고 있고 경쟁사가 있기 때문이다. 
- 엉망으로 만들면 깔끔하게 유지할 때보다 항상 더 느리다. 
- 테스트 주도 개발(TDD) 실험을 통해 제대로 작업한 일이 더 빠르다는 것을 알아냈다. 
- "빨리가는 유일한 방법은 제대로 가는 것이다."
- "자신을 과신한다면 재설계하더라도 원래의 프로젝트와 똑같이 엉망으로 내몰린다."
### 결론
- 과신을 인지하여 방지하고, 소프트웨어 아키텍처의 품질을 심각하게 고민해야 한다. 
- 비용은 최소화하고 생산성은 최대화할 수 있는 설계와 아키텍처를 가진 시스템을 만들려면, 이러한 결과로 이끌어줄 시스템 아키텍처가 지닌 속성을 알고 있어야 한다. 

## 2장. 두 가지 가치에 대한 이야기
모든 소프트웨어 시스템은 이해관계자에게 서로 다른 두 가지 가치를 제공하는데 행위(behavior)와 구조(structure)가 바로 그것이다. 
### 행위
- 첫번째 가치는 행위이다. 여기에서 행위는 기능을 뜻한다. 
- 프로그래머는 이해관계자가 기능 명세서나 요구사항 문서를 구체화할 수 있도록 돕는다. 
- 그리고 기계가 이러한 요구사항을 만족하도록 코드를 작성한다. 
- 많은 프로그래머가 이 일이 할 일의 전부라고 생각하지만 틀린 생각이다. 

### 아키텍처
- 두번째 가치는 '소프트웨어'라는 단어와 관련이 있다. 
- 소프트웨어를 만든 이유는 기계의 행위를 쉽게 변경할 수 있도록 하기 위해서이다. 
- 부드러워야하며 그 뜻은 변경하기 쉬워야 한다. 
- 변경사항을 적용하는 데 드는 어려움은 변경되는 범위(scope)에 비례해야하며, 변경사항의 형태(shape)와는 관련이 없어야 한다. 
- 아키텍처가 특정 형태를 다른 형태보다 선호하면 할수록, 새로운 기능을 이 구조에 맞추는 게 더 힘들어진다. 
- 따라서 아키텍처는 형태에 독립적이어야 하고, 그럴수록 더 실용적이다. 

### 더 높은 가치
- 소프트웨어 시스템이 동작하도록 만드는 것이 더 중요한가? 아니면 소프트웨어 시스템을 더 쉽게 변경할 수 있도록 하는 것이 더 중요할까?
- 완벽하게 동작하지만 수정이 아예 불가능한 프로그램은 요구사항이 변경될 때 동작을 하지 않게 되고 쓸모 없는 프로그램이 되어 버린다. 
- 동작은 하지 않지만 변경이 쉬운 프로그램은 동작하도록 만들 수 있고, 변경사항이 발생하더라도 여전히 동작하도록 유지보수할 수 있다. 
- 수정이 현실적으로 불가능한 시스템은 존재하기 마련인데, 변경에 드는 비용이 변경으로 창출되는 수익을 초과하는 경우이다. 
- 즉, 수정이 쉽도록 만들어야 한다.

### 아이젠하워 매트릭스
- 미국 대통령이 고안한 중요성과 긴급성에 관한 아이젠하위 매트릭스
- 행위는 긴급하지만 매번 높은 중요도를 가지는 것은 아니다. 
- 아키텍처는 중요하지만 즉각적인 긴급성을 필요로 하는 경우는 절대 없다. 
- 우선순위는 (1) 긴급하고 중요한 (2) 긴급하지는 않지만 중요한 (3) 긴급하지만 중요하지 않은 (4) 긴급하지도 중요하지도 않은 으로 분류할 수 있다. 
- 아키텍처는 가장 높은 두순위를 차지하고 행위는 1,3번째에 차지하고 있다는 사실은 인지하여야 한다. 
- 업무 관리자는 보통 아키텍처의 중요성을 평가할 만한 능력을 검비하지 못하기 때문에 개발자는 딜레마에 빠진다. 
- 기능의 긴급성이 아닌 아키텍처의 중요성을 설득하는 일은 소프트웨어 개발팀이 마땅히 책임져야한다. 

### 아키텍처를 위해 투쟁하라. 
- 개발자는 소프트웨어를 안전하게 보호해야 할 책임이 있으므로 당신 역시도 이해 관계가 있다. 
- 아키텍트는 특성과 기능을 개발하기 쉽고, 간편하게 수정할 수 있으며, 확장하기 쉬운 아키텍처를 만들어야 한다. 
- 아키텍처가 후순위가 되면 시스템을 개발하는 비용이 더 많이 들고, 일부 또는 전체 시스템에 변경을 가하는 일이 현실적으로 불가능해진다. 
