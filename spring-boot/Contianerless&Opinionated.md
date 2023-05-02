# Spring Boot 이해하는 키워드

학습자료: 토비의 스프링부트 강의, 인프런

## 1. Web Container

- Web Container는 Web Component를 관리하는 기능을 담당한다. 
- Web Component는 Dynamic Content를 제공하기 위해서 존재한다.
- Web Client의 Request를 담당할 Web Component에게 Routing 또는 Mapping을 해준다. 
- 자바에서 Web Component는 Servlet, Web Container는 Servlet Container로 보는 것이 일반적이다.


## 2. Containerless

- Servlet Container를 설정하는 것이 굉장히 복잡하다.
- 하지만 이러한 설정이 시작 단계에서 이후에서는 중요한 과정이 아니다.
- Servlet Container가 사라지는 것은 아니지만, Spring Boot를 통해서 복잡한 설정없이 Standalone Application으로 동작할 수 있도록 한다.

## 3. Opinionated(고집이 있는, 자기주장이 강한)

### 스프링 프레임워크의 설계 철학
- 극단적인 유연함을 추구, Not Opinionated, 다양한 관점을 추구, 수많은 선택지를 다 포용한다.
- 이러한 유연함은 개발자가 프로젝트를 시작할 때, 기술 선택과 설계 고민이 중요하다.

### 스프링 부트의 설계 철학
- 스프링 부트는 일단 정해주는대로 빠르게 개발할 수 있도록 Opinionated 철학을 가진다.
- 표준 자바 기술 및 오픈소스 기술의 종류와 의존관계 및 사용 버전을 정해준다.
- DI구성과 디폴트 설정값을 제공한다.

#### 하지만, 유연한 확장
- 디폴트 구성을 커스터마이징 하는 매우 자연스럽고 유연한 방법 제공
- 스프링 부트가 스프링을 사용하는 방식을 이해한다면, 언제라도 스프링부트없이 재구성 가능
- 나만의 스프링 부트 모듈을 작성할 수 있음


### 스프링 부트를 이해해야하는 이유?
- 스프링 부트가 스프링의 기술을 어떻게 활용하는지 배우고 **응용**할 수 있다.



