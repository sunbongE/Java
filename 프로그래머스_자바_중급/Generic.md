# Generic

**클래스나 메서드에서 데이터 타입을 미리 지정하지 않고, 나중에 사용할 때 타입을 지정할 수 있도록 하는 기능**이다. 이렇게 하면 컴파일러가 타입 검사를 할 수 있어서 코드의 안정성과 재사용성을 높일 수 있다.

보통 Collection 프레임워크에서 많이 사용하는데, 알고리즘 풀이할 때 자주 사용하는 Queue를 생성할 때 사용하는 것이 제네릭 이었다. 
보통 Queue<int[]>,Queue<내가만든객체타입> 으로 많이 사용했는데 아무렇지 않고 당연스럽게 사용하던 것이 제네릭이었다는 것이다. 이런 경험이 있어서 타입을 사용할때 지정한다는 것과 컴파일러가 타입 검사를 할 수 있다는 말이 더 와 닿았다.

## 제네릭 클래스 생성

(T는 정해진 이름X)

```java
package javaUtilExam;

public class Box<T> {
    private T obj;
    public void setObj(T obj){
        this.obj = obj;
    }

    public T getObj(){
        return obj;
    }
}

```

## 제네릭 클래스 사용

```java
package javaUtilExam;

public class BoxExam {
    public static void main(String[] args) {
        // Object타입을 받을 수 있게 
        Box<Object> box = new Box<>(); 
        box.setObj(new Object());
        Object obj = box.getObj();
    
        Box<String> box2 = new Box<>();
        box.setObj("문자열 타입");
        String str = box2.getObj();
        
        Box<Integer> box3 = new Box<>();
        box3.setObj(20);
        Integer age = box3.getObj();
    }
}

```
