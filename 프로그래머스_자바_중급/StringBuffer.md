## StringBuffer

StringBuffer는 자기 자신(this)을 반환한다.

메소드 체이닝 : 자기 자신을 리턴해 계속해서 자신의 메소드를 호출하는 방식. 

```java
package javaStudy;

public class StringBufferExam {
    public static void main(String[] args) {
        StringBuffer sb = new StringBuffer();
        sb.append("hello");
        sb.append(" ");
        sb.append("world");

        String str = sb.toString();
        System.out.println(str);
        StringBuffer sb2 = new StringBuffer();
        StringBuffer sb3 = sb2; // 자기 자신 this를 리턴하기 때문에
        sb3.append("hello");    // sb3에 값을 추가하는 것이 sb2에 추가하는 것과 같은 효과를 낸다.
        // 이렇게 계속 자신을 리턴하느것을 메소드 체이닝이라고한다.

        if(sb2 == sb3)
        System.out.println("sb2 == sb3");

        // StringBuffer 사용해서 String만들기.
        String str2 = new StringBuffer().append("불변 객체 String에").append(" ").append("+= 연산으로 값을 더하면").append(" 성능저하 발생하는데,\n").append("StringBuffer는 가변 객체라서 이런 문제를 해결했네").toString();
        System.out.println(str2+" "+str2.getClass());
    }
}
```

---

## String, StringBuffer, StringBuilder

| String | 불변 | 변하지 않는 문자열에 사용 |
| --- | --- | --- |
| StringBuffer | 가변 | 문자열 수정이 빈번한 경우 사용 |
| StringBuilder | 가변 | 문자열 수정이 빈번한 경우 사용 |

## StringBuffer와 StringBuilder 차이

StringBuffer는 동기화를 지원하여 멀티스레드 환경에서도 안정적으로 문자열 수정에 유리하다.

StringBuilder는 동기화를 지원하지 않아서 단일 스레드 환경에서 사용하는 것이 적합하고, StringBuffer보다 속도가 빠르다. 

생각해보면, 알고리즘 풀이할 때 StringBuffer보다 StringBuilder를 사용했는데, 그 이유를 이제야 알았다.
알고리즘 풀이에서는 멀티스레드 환경을 생각하지 않아도 되기 때문에 StringBuilder를 사용하는 것이었다.

### 동기화(synchronization)

동기화는 **여러 스레드가 같은 리소스에 접근할 때 서로 간섭하지 않도록 보장하는 메커니즘이다**. 예를 들어, 여러 스레드가 동시에 하나의 객체를 수정하려고 할 때, 한 스레드가 **작업하는 동안** 다른 스레드가 **개입**하지 **못하도록** 잠금을 걸어준다.

이러한 동기화는 `synchronized` 키워드를 통해 구현되고, Java의 `StringBuffer`는 내부적으로 모든 메서드가 동기화돼 있다. 반면에 `StringBuilder`는 동기화가 없으니 단일 스레드에서의 성능은 `StringBuffer`보다 더 빠르다.

---

## String의 문제점

반복문에서 String에 += 연산을 사용하면 성능 저하 발생한다. 이유는 String은 불변 객체이기 때문에 기존의 문자열에 새로운 문자열을 더할 때마다 내부에서는 새로운 String객체를 생성해서 더해주기 때문이다.
이런 문제를 해결하기 위해 앞서 배운 StringBuffer 혹은 StringBuilder를 사용해 해결할 수 있다.

예시 코드

 

```java
package javaStudy;

public class StringBufferExam {
    public static void main(String[] args) {
         // String 문제점 코드
         String s1 = "";
         for(int i =0; i<1000; i++){
	         s1 += "문자열추가";
         }
         
         // 해결 StringBuilder 사용.
         StringBilder sb = new StringBuilder();
         for(int i =0; i<1000; i++){
	         sb.append("문자열추가");
         }
         
    }
}

```

---

## 속도 차이 코드

```java
public class StringBufferPerformanceTest{
    public static void main(String[] args){
        // (1) String의 +연산을 이용해서 10,000개의 *를 이어붙입니다.
        //시작시간을 기록합니다.(millisecond단위)
        long startTime1 = System.currentTimeMillis();
        String str="";
        for(int i=0;i<100000;i++){
            str=str+"*";
        }
        //종료시간을 기록합니다.(millisecond단위)
        long endTime1 = System.currentTimeMillis();
        
        // (2) StringBuffer를 이용해서 10,000개의 *를 이어붙입니다.
        //시작시간을 기록합니다.(millisecond단위)                
        long startTime2 = System.currentTimeMillis();
        StringBuffer sb = new StringBuffer();
        for(int i=0;i<100000;i++){
            sb.append("*");
        }
        //종료시간을 기록합니다.(millisecond단위)
        long endTime2 = System.currentTimeMillis();
        
        // StringBilder 사용.
        long startTime3 = System.currentTimeMillis();
        StringBuilder builder = new StringBuilder();
        for(int i=0;i<100000;i++){
            builder.append("*");
        }
        long endTime3 = System.currentTimeMillis();
        
        
        
        // 방법(1)과 방법(2)가 걸린 시간을 비교합니다.
        long duration1 = endTime1-startTime1;
        long duration2 = endTime2-startTime2;
        long duration3 = endTime3-startTime3;
        
        System.out.println("String의 +연산을 이용한 경우 : "+ duration1);
        System.out.println("StringBuffer의 append()을 이용한 경우 : "+ duration2);
        System.out.println("StringBuilder의 append()을 이용한 경우 : "+ duration3);
    }
}
```

**결과**

String의 +연산을 이용한 경우 : 1191

StringBuffer의 append()을 이용한 경우 : 4

StringBuilder의 append()을 이용한 경우 : 3

---
