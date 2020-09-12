# (공부용) Python-Microservices-Demo
[Python으로 클린 아키텍처 적용하기](https://velog.io/@jahoy/Python%EC%9C%BC%EB%A1%9C-Clean-Architecture-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0)

![Screen Shot 2020-09-13 at 12 10 49 AM](https://user-images.githubusercontent.com/50973416/92998617-b2434600-f555-11ea-838d-3ef50bbf15a8.png)

## aution 경매를 microservice로 적용한 예
    1. event sourcing방식으로 aution 에서 발생하는 event에 따라 event_bus는 각각에 해당하는 handler로 command를 보내서 동작시킴.
    
    2. CQRS(Command Query Responsibility Segregation) 방식 도입: Command는 상태 업데이트, Query는 denormalized된 데이터를 읽기만.
    
    3. dependency injection을 통해 decoupled된 아키텍처를 유지. (external world->infrastructure->appliction->domain)
    
    4. facade, factory 패턴등을 통해 usecase를 구성하고 동작시킴.
    
    5. port-adapter 패턴을 통해 3rd party 또는 다른 도메인과 decoupled된 채로 통신.

    6. saga 패턴을 이용해 복잡한 비즈니스 로직을 처리함.


# 실행법
```bash
docker-compose up --build
```

# 폴더구조:
    autions: 경매
    aution_infastructure: 경매관련 infra(repositories, queries)
    customer_relationship: 경매 관련 이메일 발송
    foundation: 이 프로젝트에서 자주 공통적으로 쓰이는 함수 라이브러리 
    payments: 결제(3rd party)
    shipping: 배송
    shipping_infrastructure 배송관련 infra(repositories, queries)
    processes: 각기 다른 모듈에서 들어온 event들을 한곳에서 처리하는 Saga(State Design Pattern)
    wepapp: 웹앱
