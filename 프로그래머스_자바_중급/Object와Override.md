`equals` : 객체가 가진 값을 비교할 때 사용

`toString` : 객체가 가진 값을 문자열로 반환

`hashCode` : 객체의 해시코드 값 반환

```bash
package javaStudy;

import java.util.Objects;

public class Student {
    String name;
    String number;
    int birthYear;

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return Objects.equals(number, student.number);
    }

    @Override
    public int hashCode() {
        return Objects.hash(number);
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", number='" + number + '\'' +
                ", birthYear=" + birthYear +
                '}';
    }

    public static void main(String[] args) {
        Student s1 = new Student();
        s1.name = "taeho";
        s1.number = "1234";
        s1.birthYear = 1996;

        Student s2 = new Student();
        s2.name = "taeho";
        s2.number = "1234";
        s2.birthYear = 1996;

        if(s1.equals(s2)){
            System.out.println("같다.");
        }else {
            System.out.println("다르다.");
        }

        // object가 구현한 메서드를 사용하기 때문에 두 값은 다르다.
        System.out.println(s1.hashCode());
        System.out.println(s2.hashCode());
        // 같게 하기위해서는 오버라이딩 해서 사용한다.

        System.out.println(s1.toString());
    }
}

```
