# Math.round()

> 원하는 자리수에 반올림하는 방법
>
> ※ 타입이 다른 두 값을 계산할 때 범위가 큰 타입으로 형변환 후 계산이 된다.



자바에서 반올림은 파이썬과는 느낌이 많이 다른 것 같다. 뭔가 딱딱한 기계 느낌이랄까

```java
class test {
	public static void main(String args[]) { 
		double pi = 3.141592; 
		double shortPi = Math.round(pi * 1000) / 1000.0;
		System.out.println(shortPi); // 3.142
		
		//아래 과정을 통해 값이 나온다.
		System.out.println(pi); 		//3.141592
		System.out.println(pi*1000);	//3141.592
		System.out.println(Math.round(pi * 1000)); //3142 소수 첫자리에서 반올림
		System.out.println(Math.round(pi * 1000)/1000); // 타입이 int라서 3이나온다.
        // 그래서 double타입으로 계산, 3.142 
		System.out.println(Math.round(pi * 1000)/1000.0); 

        //아래와 같은 방법도 가능함.
		System.out.println((double)Math.round(pi * 1000)/1000); // 3.142
	
	}
}
```





이번에는 내림 구현

```java
class test {
	public static void main(String args[]) { 
		double pi = 3.141592; 
	
		// 3.141 을 얻으려면 값 손실시키는 방법을 통해서 얻을 수 있다.
		System.out.println(pi); 		//3.141592
		System.out.println(pi*1000);	//3141.592
		
		//실수형 타입을 정수로 변경하면서 값 손실 발생
		System.out.println((int)(pi*1000));	//3141 
		System.out.println((int)(pi*1000)/1000.0);	//3.141 double형변환
		
	}
}
```



서로 다른 타입을 연산했을 때 특징을 모르면 이해할 수 없는 개념인 것 같다.

