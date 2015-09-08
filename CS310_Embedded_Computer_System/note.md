> 2015-09-01

### Meta

Office: E3-1 4403
email: maeng@kaist.ac.kr
Office Hour: 화목 4시 ~ 5시 반 | 메일 보내고

__랩 시간 : 목요일 7시 ~ 10시__

### Embedded Systems?

임베디드 시스템이 뭐냐? PC/Server 등의 General purpose computing system이 아닌
다른 장치에 내장(embedded)되어 돌아가는 Embedded computing system.

기본적인 구조는 같다. 하지만 보다 거대한 시스템에 내장되어 특정 기능만을
수행하고, 주로 환경(real time environment)에 반응한다. Not a strictly definable
term anyway.

> 보통의 프로그램에서는 실행 시간이 correctness 보다는 performance의 문제가
되지만, 임베비드 시스템에서는 그 반대가 될 수도.

### Motivation

IT의 미래라고 불리는
- 유비쿼터스 컴퓨팅
- pervasive(?) 컴퓨팅
- ambient intelligence
- disappearing computer
- IoT

등등 전부 임베디드(+ 통신 기술)가 기반이 됨. 임베디드 킹왕짱!! Cyber-Physical
System(CPS) = Embedded System(ES) + physical environment

# 오늘 수업은 필기를 안 해도 될 것 같다.

> 2015-09-03

요새 기술이 좋아져서 얼마나 기술 좋은 임베디드 시스템 구현하려 하든지 구현의
비용에는 큰 차이가 없다 (cost of implementation<-> functionality : independent)

### Dependability
Many CPS are safety-critical
- reliability R(t) : t=0에서 정상 작동할 때 시간 t에서도 정상적으로 작동할 확률
- maintainability M(t) : 에러가 난 이후 d time unit이 지난 후 정상적으로 작동할
    확률
- availability A(t) : 시간 t에서 정상 작동할 확률
- safety, security

Availability = MTBF / (MTBF + MTTR)

### Efficiency
CPS & ES must be efficient
- code-size efficient
- run-time efficient
- weight efficient
- cost efficient
- energy effi
