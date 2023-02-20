# print 



## println의 단점

- 출력 형식을 지정할 수 없다.
- 10진수로만 출력된다.

이런 불편함을 해결해 주는 것이 printf이다.

## printf

> 여러 지시자를 사용해서 출력 형식을 지정할 수 있다.

| **지시자** | **기능**                        |
| ---------- | ------------------------------- |
| **%b**     | **boolean 형식으로 출력**       |
| **%d**     | **10진 정수 형식으로 출력**     |
| **%o**     | **8진 정수의 형식으로 출력**    |
| **%x, %X** | **16진 정수의 형식으로 출력**   |
| **%f**     | **부동 소수점의 형식으로 출력** |
| **%e, %E** | **지수 표현식의 형식으로 출력** |
| **%c**     | **문자 형식으로 출력**          |
| **%s**     | **문자열 형식으로 출력**        |



실습

```java
// 각 진수 표현식
System.out.printf("%d%n",16); // 16
System.out.printf("%#o%n",16); //  020 #을 이용해 각 진수로 출력 가능
System.out.printf("%#x%n",16); // 0x10

// Integer.toBinaryString()함수에 값을 넣으면 2진수로 값을 바꿔준다.
System.out.printf("%s%n",Integer.toBinaryString(15));  // 1111

 
float f = 123.456789f;
// 123.456787 앞에서부터 7개의 값만 정확하다. float의 정밀도가 7이기 때문이다.
System.out.printf("%f%n",f); 

double d = 123.456789;
//123.456789 double의 정밀도가 15이기때문에 전부 정확한 값이 나왔다.
System.out.printf("%f%n",d);

System.out.printf("%e%n",d); //1.234568e+02

System.out.printf("%g%n",d); // 123.457

// 정수 출력 및 정렬
System.out.printf("[%d]%n",10);

// %5d 라는 것은 5자리 정수로 지시한 것이다. 값이 10 이지만 5자리를 출력한다.
System.out.printf("[%5d]%n",10); // [   10]오른쪽 정렬해서 값이 출력
System.out.printf("[%-5d]%n",10); // [10   ]왼쪽 정렬해서 값이 출력
System.out.printf("[%5d]%n",1234567); //[1234567] 범위를 초과해도 전부 출력된다.

double d = 1.23456789;
// 14개중 소수점10자리까지 표현 왼쪽은 공백으로 오른쪽은 0으로 채워진다.
System.out.printf("[%14.10f]%n",d); //  [  1.2345678900]
System.out.printf("[%14.6f]%n",d); //  [      1.234568]
System.out.printf("[%.10f]%n",d); //  [1.2345678900]

System.out.printf("[%s]%n","www.navse.com");//[www.navse.com]

System.out.printf("[%20s]%n","www.navse.com"); //[       www.navse.com]

System.out.printf("[%-20s]%n","www.navse.com"); //[www.navse.com       ]

System.out.printf("[%10s]%n","www.navse.com"); //[www.navse.com]

System.out.printf("[%.10s]%n","www.navse.com"); //[www.navse.]
// .을 사용한 문자열은 개수만큼만 출력한다.

```

