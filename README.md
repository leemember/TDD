# TDD (테스트 방법론)
> 테스트 주도 개발과 자바스크립트 디자인 패턴에 대해 알아보자. 리팩토링하며 적용해보며 결국에는 좋은 품질의 코드를 만들 수 있다.

<br>

### 개념
1. 단위(unit)
- 특정 조건에서 어떻게 작동해야 할지 정의
- '함수'로 표현한다.
- 준비, 실행, 단언 패턴을 따른다.

어떤 함수를 만든다고 가정해본다면, 기능을 테스트할 수 있는 테스트 코드를 만듭니다.
- 적색 : 테스트할 수 없는 단계🖐
- 녹색 : 테스트에 통과할 수 있는 단계🖐 함수의 기능 코드를 작성한다. 
- 리팩터 : `내가 작성한 코드가 확실하다`라고 할 수 있는 단계🖐 코드 품질이 높아진다.

### 설치
자바스크립트에는 `재스민` 이라는 프레임워크를 사용
> https://jasmine.github.io/pages/getting_started.html

### 두가지 설치 방법
- 스탠드얼론 (브라우저에 직접 올린다. 실무에서 많이 사용하진 않는다.)
- 카르마 (자동화 해준다. 실무에서 많이 사용한다.)

### 스탠드얼론
- 먼저 스탠드얼론으로 설치를 해보자.

### 테스트 러너란?
- 재스민, 소스, 테스트 코드를 실행하는 것이다.
- 스탠드 얼론으로 설치한 자스민은 HTML 파일이 테스트 러너다.

--------------

### 모듈 패턴
- ⭐️ 임의 모듈 패턴
- 즉시 실행 함수 패턴
    - 싱글톤이다.

### 모듈 생성 원칙
- 단일 책임 원칙에 따라 모듈은 한 가지 역할만 한다.
    - 그 역할만 집중함으로서 모듈을 더욱 튼튼하게 만들고 테스트 하기에도 쉽다.
- 모듈 자신이 사용할 객체가 있다면 의존성 주입 형태로 제공한다.
    - 테스트가 쉽다.
    - 팩토리 주입형태로 제공한다.

### 테스트 더블
- 단위 테스트 패턴으로 테스트하기 곤란한 컴포넌트를 대체하여 테스트한다. 특정 동작을 흉내만 낼뿐이지만 테스트하기는 적합하다.
    - 더미 : 인자를 채우기 위해 사용
    - 스텁 : 더미를 개선하여 실제 동작하게끔 만드는것. 리턴값을 하드 코딩한다.
    - 스파이 : 스텁과 유사하다. 내부적으로 기록을 남기는 추가 기능
    - 페이크 : 스텁에서 발전한 실제코드. 운영에서는 사용할 수 없다.
    - 목 : 더미, 스텁, 스파이를 혼합한 형태이다.

자스민에서는 이런 테스트 더블을 '스파이시'라고 부른다.

#### 테스트 코드 작성 방식

```
it('클릭 이벤트 발생시 increseAndUpdateView실행', () => {
  spyon(view, 'increseAndUpdateView')
  //click !
  expect(view.increseAndUpdateView).toHaveBeenCalled()
  })
```

클릭 이벤트 핸들러를 바인딩할 돔 엘리먼트를 주입받자 ❗️

