# Java 기초

> 자바에서 모든 문장은 세미콜론으로 끝나야한다.

- print() : 출력 후 줄바꿈을 하지 않음
- println() : 출력 후 줄바꿈을 합니다.



```java
public class Ex2_1 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println(3+5); // 덧셈	8
		System.out.println(5-3); // 뺄셈	2
		System.out.println(3*5); // 곱셈	15
		System.out.println(5/3); // 나눗셈	1
		System.out.println(5/3.0); // 나눗셈	1.6666666666666667
	}

}
```



## 변수(variable)

하나의 값을 저장할 수 있는 메모리 공간이다.

변수 선언 이유: 값을 저장할 공간을 마련하기 위함

### 자바에서 변수 선언

```java
변수타입 변수이름;
int age; // 정수타입 변수의 공간이 만들어졌다.
```



### 변수에 값 저장하기

```java
int age;	
age = 28;	// 변수 age에 28저장
```



### 변수의 초기화

모든 변수 사용하기 전에 적절한 값으로 초기화하는 것이 좋다.

그래서 대부분 선언과 동시에 초기화를 한다.

```java
int x = 0;
int y = 5;
int x = 0, y = 5; // 위 두 줄은 이런식으로 한줄로 입력할 수 있다.
```

- 클래스 변수 

- 인스턴스 변수

- 지역 변수 
  - 자동 초기화되지 않기 때문에 **값을 읽기 전에 반드시 초기화를 해주는 것이 좋다.**
    컴파일할 때 에러가 발생할 수 있기 때문

### 변수의 값 읽어오기

```java
int year = 0, age = 14;
year = age + 2000; // year = 2014

age = age+1 // 자신을 1증가 시키는 방법 
System.out.println(age); // age = 15
```



### 사칙연산

```java
public class VarEx1 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int x = 4, y = 2;
		System.out.println(x+y);
		System.out.println(x-y);
		System.out.println(x*y);
		System.out.println(x/y);
	}

}
```



## 변수의 타입

| 표현   | 내용 |
| ------ | ---- |
| int    | 정수 |
| char   | 문자 |
| double | 실수 |
|        |      |



### 값의 타입

자바에는 값의 타입이 8 개 있다. 

- 값
  - 문자
  - 숫자
    - 정수 - byte, short, int, long
    - 실수 - float, double
    - 논리 - boolean
      - true
      - false

## 상수

값을 한번만 저장할 수 있는 변수

처음에 저장한 값을 다른 변수로 **바꿀 수 없다**는 뜻

선언 방법 - 변수 선언 앞에 final을 붙인다.

```java
final int _max = 100; // 이거 상수
max = 200; // 에러
```

![image-20230215182924717](Java%EA%B8%B0%EC%B4%88.assets/image-20230215182924717.png)

score2 를 상수로 만들고 값을 재할당하면 에러가 난다.



## 리터럴

그 자체로 값을 의미하는 것이다.

```java
final int _max = 100; // 이거 상수
max = 200; // 에러
```

위 코드에서 100,200 등 그 자체가 값인 것을 의미한다.