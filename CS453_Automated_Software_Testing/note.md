# CS453 Automated Software Testing

> 2015-09-01

### Meta

출석/참여/퀴즈 20%, 과제 50%, 중간 15%, 기말 15% : 숙제가 매우 중요할 예정

It will take about 10+ hours for each assignment for middle level C/C++
programmar

400번대이므로 OS를 들었을거라 가정;;;한다

영어수업이라 총장님한테 혼나기 싫으니까 숙제랑 과제랑 전부 영어로 써서 내세요
아니면 10% 패널티

교과서는 딱히 없다. 지금 올라와 있는 강의자료들 다 outdated니까 강의 바로 전에
업데이트 하겠음

### Course Intro

Automated SW Testing - the most important keyword is __Automated__

한국에서는 소프트웨어를 장인정신의 산물이라 생각한다. 정부등에서 소프트웨어가
창의력이랑 관련된, 뭔가 굉장한 것이라고 생각한다. 'SW 마에스트로'라는 단어를
보라.

하지만 내가 생각했을 땐 소프트웨어는 과학이다. 장인정신 같은게 아니라 과학적인
방법으로 접근해야 한다. 누가 복수전공을 6개월만에 해서 삼성에 취직했다 그러면
안 믿을거면서 C/C++ 공부 6개월만 한 천재가 그런다면 왜 거부감이 없냐.

프로그래밍은 3~4개월 언어 문법 배우면 할 수 있는거라고 착각하는데, 절대 아니다.
1층짜리 집 짓는데에 별 기술이 필요없다고해서 건축이 얕은 분야가 아니듯. 건축 한
일년 배우고 육삼빌딩 지을 수 있냐?

리눅스를 비롯해 너희가 쓰고 있는 프로그램들 LoC가 몇백만줄인데 그거 정열과
끈기로 짜고 정열과 끈기로 수동 테스트? 말이 안 된다.

이 클래스에서 소프트웨어가 얼마나 복잡하고 어려운지, 테스팅이 얼마나 어려운
것인지를 체감하고 가면 절반 이상 성공. magic answer를 줄 수는 없지만 어떤
어려움들이 있고 어떤 해결 시도들이 있었는지.

수업의 목표
- SW 테스팅의 테크닉
- SW의 복잡성 체감하기 :  겁나게 복잡함!! 다른 어떤 공학적인 산물보다도

intel CPU 같은거 생각해봐. 엄청 복잡한데 그 이유는 loop & descrete.. 물리 세계에
있는 값들은 대부분 continuous 한데 SW 상에서는 한 순간 1000이던 값이 어떤 징조도
없이 다음 라인에서 -1000이 되도 이상할게 없다.

제트기에 들어 있는 코드의 LoC가 1960: less than 10M -> 2012: more than 80M...
이제 어디에든 SW가 들어있다.

하지만 소프트웨어의 poor quality로 인해 수많은 안전 문제들이 발생함. 예를 들어
어떤 방사능 치료 기계에서 concurrency 문제로 종종 방사능을 overdose해서 환자가
죽는 경우들이 있었음. concurrency bug는 non-deterministic 하기 때문에 찾는데
한참 걸렸고, 만든 회사는 파산.

그 외에도 도요타 자동차의 급발진, 여러 비행기, 위성등에서 SW의 결함으로 인한
치명적인 사고들이 계속 생겨나왔음. <역사 속의 소프트웨어 오류>

도요타 버그 보면 buffer overflow, invalid pointer, race condition, nested
scheduler unlock, unsafe casting, stack overflow 죄다 났다. 숙제할 때 많이 봤지?
숙제 할 때야 점수 낮게 받고 그만이지만 실제 생활에서는 사람이 죽는다. 인식을
바꿔야함.

이빨 하나 썩어도 괴로워하면서 소프트웨어에 버그들이 득실거리는 걸 왜 안
괴로워하니? 잡아야 돼 이 친구들아. 땅에 떨어진거 집어먹고 손도 안 씻고 밥
먹을거야?? 지금은 SW 중세.

### Main Target

임베디드 시스템. highly reliable SW technology is a key to the success

임베디드에서 버그 나면 좀 더 재앙적인 결과가 나옴. 수술 로봇의 프로그램에 버그가
난다면? 자동차 소프트웨어에서의 버그? 로켓? 임베디드는 복잡하고 sw correctness에
대한 니즈가 훨씬 크다.

characteristics of embedded SW
- concurrent
- optimized : far more complex
- directly connected w/ acting HW

한국은 IT 강국이지만, 항상 time-to-market과 sw quality 간의 갈등, 보통 전자를
선택함.

two domains of embedded sw
- consumer electronics
- safety critical systems

어디냐에 따라 방법론등이 많이 달라짐. 우리나라는 SW 상의로는 consumer
electronics 분야에 훨씬 강함. 그래서 우리 수업도 그쪽에 집중할거.

### Practicalness

삼성사에서 개발한 임베디드 C 프로그램 테스트를 위해 Concolic unit test tool인
CONBOL 개발. 400만원 좀 넘게 들여서(??) 삼성에서 상도 여러개 받고 논문 4편 냄.
산업이랑 학계에서 둘 다 인정받는 분야.

we can verificate...
- 네트워크 프로토콜
- 홈 서비스
- 플래시 메모리
- 스마트폰 sw

실질적으로 사용될 곳이 엄청 많음. 이 클래스에서 배우는거 학교에서 수업듣고
과제하려는게 아니라 실제 필드에서 엄청 많이 쓰이는거야. 내가 암.

### Research Trend

임베디드 시스템 개발은 학문적으로 stable stage에 있음. 타겟 시스템에다가 기능
하나 추가하는거는 더이상 academic contribution으로 인정되지 않음.

연구의 초점이 이제 시스템의 퀄리티를 높이는 쪽으로. energy efficient,
ez-maintenance, and __correctness__

USENIX Security 2015, ICSE 2014, ASPLOS 2011 최고 논문상 전부 SW 테스트/검증
관련 논문들. 꼭 이쪽 분야에서 일 안 하더라도 어디서든 이 과목의 지식은
유용할거임.

### Tool-based

Code Analyzer
- C/C++ AST parser: Clang
- Language independent Intermediate representation(IR): LLVM

Model Checker
- Explicit model checker: Spin

Software model checker
- Bounded model checker for C program: CBMC

Satisfiability solver
- MiniSAT

Satisfiability Module Solver
- Yices
- Z3

Concolic testing tool
- CREST

> 2015-09-03

### Necessity of Systemic & Automated Testing Techniques - Fight the **Complexity**

소프트웨어는 겁나게 무섭고 귀찮은 녀석이여... 요정이라기보단 괴물, 용 같은 녀석.
우리는 소프트웨어의 복잡성과 싸워야 할 필요가 있단다. 그러기 위해 체계적인 +
자동화된 방법이 필요행행행

빌게이츠가 말하기를 MS에 개발자만큼이나 테스터가 많다. 실제로 인적 자원이
테스팅에 개발보다 3배가 더 들어감!!! 또한 테스팅 관련 LoC = 3 * 실제 프로그램
LoC..

소프트웨어 = 마법진.. 개발자/마법사가 지식을 가지고 한땀한땀 짜서 실제 코드/마법
보다 훨씬 복잡/막대한 결과를 만들어내고, 예상되거나 제어되지 않는, 에러/재앙이
발생함.

### Ex) Testing a Triangle Decision Program

삼각형의 세 변의 길이가 주어진 채로 부등변/이등변/정 삼각형인지를 만들어봐라.
라는 문제에 대한 테스트 케이스를 만들어봐라.

#### Precondition (Input Validity) Check
- a, b, c > 0
- a is smaller than b + c (and so on..)
- type check
- overflow...

사람은 창의적인/가치 판단적인 부분에는 강하지만 이런 본질적이지 않은, 세세한
부분들을 체크하는데에는 상대적으로 약하다.

decision tree를 전부 그렸다고 할 때, 테스트 케이스를 총 몇 개 만들어야 할까?
분명한 건 스펙에 있는 케이스들에 대해 하나씩 만드는 걸로는 분명 부족함...!!!
스펙 -> 실제 코드로 가면서 abstraction이 적어질수록 해당 단계를 위한 테스트는
훨씬 많아지고 빡세짐.

테스트 케이스의 크기 -> #(feasible unique execution paths)

비행기 안 타면 미국으로 못 날아간다고 슬퍼하니? 아니잖아. 근데 왜
디버깅/테스팅은 그 좋은 도구들 냅두고 printf로 장인정신 가지고 하려고 하니??

CPU, 자동차 같은 제품들은 warranty가 존재.. 소프트웨어에는 그런게 없지 않니?
Instead, **use it at your own risk** (내 생각에 이건 좀.. 계속 update 하고 bug
fix 하는데)

### More Complex Testing Situation
- 길이가 인티저가 아니라 플로팅 넘버라면? (round-off errors)
- 직각 삼각형인지도 체크해야 된다면?

이런 상황에서,
- 앞서서 작성한 테스트를 다시 돌려봐야 하는가? 또는, 아예 처음부터 다시
    짜야되나?
- 타겟 프로그램의 변경된 부분만 체크할 수 있는, 미니멀한 테스트를 만들고 싶음.

**Regression Testing** is essential ! ! !
- 프로그램을 수정하면서 영향을 받은 부분을 어떻게 알 수 있나?
- 그 부분들을 커버하는 테스트 케이스들을 어떻게 만드나?
- 그 테스트 케이스들을 어떻게 효율적으로 만드나?
- 앞서 짜놨던 현존하는 테스트케이스들을 어떻게 재사용하나?

모든 케이스를 다 커버했다고 생각해도 빈틈이 있을 수 있다...
-> model checking: analyzes all possible inputs

테스팅보다 test oracle이 더 중요할수도 ? ? ?? ?  ? : importance of proper assert

### Concurrency
Concurrent programs is highly complex because: non-deterministic scheduling
Total 20 interleaving scenarios : 6! / (3! * 3!) However, only 11 unique outcomes

`C
int x=0, y=0, z=0;
void p() {x=y+1; y=z+1; z=x+1;}
void q() {y=z+1; z=x+1; x=y+1;}
`

위의 케이스에서 z는 6도 되는데 y는 6은 커녕 5도 될 수 없음... 너희 이럴거라
생각했니? 3줄짜리 프로그램도 예상 못 하는데 훨씬 복잡한 프로그램은?

Mutual Exclusion Algorithm < 이거 찾아보자
Data race bugs, Atomicity bugs 이것들도... 는 이 수업에서 안 한다네요


