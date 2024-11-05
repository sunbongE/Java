# java.lang패키지/오토박싱
java.lang패키지는 import하지 않고도 사용할 수 있다.

- wrapper
    - 8개의 기본 타입을 객체로 변환시킨다.
    - 8개의 기본 데이터 타입의 맵핑되는 각각의 클래스들을 모두 모아서 래퍼클래스라고 한다.
- Object :  최상위 클래스
- String
- StringBuffer
- StringBuilder
- System
- Math

**오토박싱** 

기본타입을 객체 타입으로 선언할 때 자동으로 wrapper로 감싸주어 객체타입으로 변환을 해주는 것

```bash
int n1 = 5;
Integer n2 = n1; // 오토박싱 
```

**오토언박싱**

객체 타입을 기본타입에 선언했을 때 자동으로 기본타입으로 변환해주는 것

```bash
Integer n1 = 5; // 오토박싱
int n2 = n1;    // 오토언박싱
```
