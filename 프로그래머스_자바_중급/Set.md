# Set
**특징** : 순서가 없고, 중복 허용 안함

# HashSet

### `HashSet` 주요 메서드와 시간복잡도

| 메서드 | 역할 | 평균 시간복잡도 | 최악 시간복잡도 |
| --- | --- | --- | --- |
| `add(E e)` | 값을 추가하고, 추가 성공 시 `true`, 이미 있으면 `false` 반환 | O(1) | O(n) |
| `remove(Object o)` | 값을 제거하고, 성공 시 `true`, 없으면 `false` 반환 | O(1) | O(n) |
| `contains(Object o)` | 값이 존재하면 `true`, 없으면 `false` 반환 | O(1) | O(n) |
| `size()` | 저장된 요소의 개수를 반환 | O(1) | O(1) |
| `isEmpty()` | `HashSet`이 비어 있으면 `true`, 아니면 `false` 반환 | O(1) | O(1) |
| `clear()` | 모든 요소를 제거 | O(n) | O(n) |
| `iterator()` | 요소를 순회할 수 있는 `Iterator` 반환 | O(1) | O(1) |

### HashSet의 시간복잡도

- **평균 시간복잡도 O(1)**: `HashSet`의 `add`, `remove`, `contains` 메서드는 대부분의 경우 O(1)로 동작합니다. 해시 함수가 잘 설계되어 있어 해시 충돌이 적을 때, 즉 데이터가 해시 테이블에 균등하게 분포할 때 O(1) 성능이 나오기 때문이다.
- **최악 시간복잡도 O(n)**: 최악의 경우, 해시 충돌이 많아지면 `HashSet` 내부에서 여러 값이 같은 해시 버킷에 저장될 수 있습니다. 이 경우 `HashSet`은 연결 리스트처럼 동작하게 되고, 특정 요소를 검색하거나 추가, 삭제하는 데 O(n)의 시간이 걸릴 수 있습니다. 하지만 일반적인 상황에서는 이 최악의 경우가 드물기 때문에 `HashSet`은 대부분 빠르게 동작하는 편입니다.

### HashSet 사용 팁

- **중복을 허용하지 않음**: `HashSet`은 데이터의 중복을 허용하지 않기 때문에, 데이터의 중복을 방지하고자 할 때 유용합니다.
- **빠른 검색과 추가**: 주로 검색과 추가가 자주 발생하는 상황에서 `HashSet`은 좋은 성능을 발휘합니다.
- **순서가 중요하지 않은 경우 사용**: `HashSet`은 순서가 중요하지 않은 경우 적합합니다. 요소의 순서를 유지하려면 `LinkedHashSet`이나 `TreeSet`을 사용하는 것이 좋습니다.
- **사용 코드**
    
    ```java
    package javaUtilExam;
    
    import java.util.HashSet;
    import java.util.Iterator;
    import java.util.Set;
    
    public class HashSetExam {
        public static void main(String[] args) {
            Set<String> set = new HashSet<>();
            boolean a = set.add("a");
            boolean b = set.add("b");
            boolean c = set.add("a");
    
            // Iterator 사용한 출력
            System.out.println("Iterator 사용");
            Iterator<String> iter = set.iterator();
            while(iter.hasNext()){
                System.out.println(iter.next());
            }
    
            System.out.println("for each사용");
            // for each 사용한 출력
            for (String s : set) {
                System.out.println(s);
            }
    
            System.out.println(a); // true
            System.out.println(b); // true
            System.out.println(c); // a와 중복되어 false
        }
    }
    ```
    
    **결과**
    
    Iterator 사용
    a
    b
    for each사용
    a
    b
    true
    true
    false
    

---

# TreeSet

`TreeSet`은 자바의 **이진 탐색 트리** 구조를 기반으로 한 컬렉션 클래스입니다. `TreeSet`은 정렬된 순서를 유지하면서 데이터를 저장하고, 중복된 값을 허용하지 않아요. `TreeSet`은 특히 **범위 탐색**과 **정렬**이 필요한 경우에 유리합니다. 기본적으로 오름차순 정렬을 적용하며, 사용자 지정 Comparator를 통해 원하는 방식으로 정렬할 수도 있습니다.

### `TreeSet` 주요 메서드와 시간복잡도

| 메서드 | 역할 | 평균 시간복잡도 | 최악 시간복잡도 |
| --- | --- | --- | --- |
| `add(E e)` | 값을 추가하고, 추가 성공 시 `true`, 이미 있으면 `false` 반환 | O(log n) | O(log n) |
| `remove(Object o)` | 값을 제거하고, 성공 시 `true`, 값이 없으면 `false` 반환 | O(log n) | O(log n) |
| `contains(Object o)` | 값이 존재하면 `true`, 없으면 `false` 반환 | O(log n) | O(log n) |
| `size()` | 저장된 요소의 개수를 반환 | O(1) | O(1) |
| `isEmpty()` | `TreeSet`이 비어 있으면 `true`, 아니면 `false` 반환 | O(1) | O(1) |
| `clear()` | 모든 요소를 제거 | O(n) | O(n) |
| `iterator()` | 요소를 순회할 수 있는 `Iterator` 반환 | O(1) | O(1) |
| `first()` | 첫 번째(최소) 요소 반환 | O(log n) | O(log n) |
| `last()` | 마지막(최대) 요소 반환 | O(log n) | O(log n) |

### TreeSet의 시간복잡도

- **평균 및 최악 시간복잡도 O(log n)**: `TreeSet`은 이진 탐색 트리 기반으로 동작하기 때문에, 요소 추가, 제거, 탐색 시 O(log n)의 시간복잡도를 가집니다. 이는 데이터의 크기에 비례하여 성능이 결정되며, 균형이 잘 맞는 트리에서는 대부분 O(log n) 성능을 보장합니다.
- **정렬이 필요한 경우 적합**: `TreeSet`은 요소를 정렬된 상태로 유지하기 때문에, 정렬을 위해 별도의 연산을 할 필요가 없습니다. 또한, 범위 탐색 기능이 제공되어 특정 구간에 속하는 요소들을 쉽게 찾을 수 있습니다.

### TreeSet 사용 팁

- **중복을 허용하지 않음**: `TreeSet`은 데이터의 중복을 허용하지 않으므로 중복을 방지하고자 할 때 유용합니다.
- **정렬된 순서를 유지**: 데이터가 자동으로 오름차순 정렬되기 때문에 정렬이 필요한 경우에 적합합니다.
- **범위 탐색 가능**: 특정 범위에 속하는 데이터들을 쉽게 탐색할 수 있어, 정렬된 데이터를 자주 다룰 때 유리합니다.
- **사용 코드**
    
    ```java
    package javaUtilExam;
    
    import java.util.Iterator;
    import java.util.NavigableSet;
    import java.util.Set;
    import java.util.TreeSet;
    
    public class TreeSetExam {
        public static void main(String[] args) {
            // TreeSet 생성 및 값 추가
            TreeSet<Integer> set = new TreeSet<>();
            set.add(10);
            set.add(20);
            set.add(30);
            set.add(40);
            set.add(50);
    
            // Iterator 사용한 출력
            System.out.println("Iterator 사용:");
            Iterator<Integer> iter = set.iterator();
            while (iter.hasNext()) {
                System.out.print(iter.next() + " ");
            }
            System.out.println();
    
            // for each 사용한 출력
            System.out.println("for each 사용:");
            for (Integer num : set) {
                System.out.print(num + " ");
            }
            System.out.println();
    
            // 특정 요소 탐색
            System.out.println("contains(30): " + set.contains(30)); // true
            System.out.println("contains(60): " + set.contains(60)); // false
    
            // 최소 및 최대 요소 조회
            System.out.println("최소값 (first): " + set.first()); // 10
            System.out.println("최대값 (last): " + set.last());   // 50
    
            // 범위 탐색 (부분 집합)
            System.out.println("30 이상 50 미만의 값들 (subSet): " + set.subSet(30, 50)); // [30, 40]
    
            // headSet과 tailSet 사용
            System.out.println("40 미만의 값들 (headSet): " + set.headSet(40)); // [10, 20, 30]
            System.out.println("30 이상의 값들 (tailSet): " + set.tailSet(30)); // [30, 40, 50]
    
            // 내림차순 정렬된 Set 생성
            NavigableSet<Integer> descendingSet = set.descendingSet();
            System.out.println("내림차순 (descendingSet): " + descendingSet); // [50, 40, 30, 20, 10]
    
            // 값 제거
            set.remove(30);
            System.out.println("30 제거 후 (remove): " + set); // [10, 20, 40, 50]
    
            // clear 메서드를 사용해 모든 요소 제거
            set.clear();
            System.out.println("모든 요소 제거 후 isEmpty: " + set.isEmpty()); // true
        }
    }
    
    ```
    

### TreeSet의 특이한 메서드와 시간복잡도

| 메서드 | 역할 | 평균 시간복잡도 | 설명 |
| --- | --- | --- | --- |
| `ceiling(E e)` | 지정한 값 이상인 요소 중 최소값 반환 | O(log n) | `e`와 같거나 큰 값 중 가장 작은 값을 반환. 없으면 `null` |
| `floor(E e)` | 지정한 값 이하인 요소 중 최대값 반환 | O(log n) | `e`와 같거나 작은 값 중 가장 큰 값을 반환. 없으면 `null` |
| `higher(E e)` | 지정한 값보다 큰 요소 중 최소값 반환 | O(log n) | `e`보다 큰 값 중 가장 작은 값을 반환. 없으면 `null` |
| `lower(E e)` | 지정한 값보다 작은 요소 중 최대값 반환 | O(log n) | `e`보다 작은 값 중 가장 큰 값을 반환. 없으면 `null` |
| `pollFirst()` | 첫 번째(최소) 요소 반환 및 제거 | O(log n) | 가장 작은 값을 반환하고 `TreeSet`에서 제거 |
| `pollLast()` | 마지막(최대) 요소 반환 및 제거 | O(log n) | 가장 큰 값을 반환하고 `TreeSet`에서 제거 |
- **사용 코드**
    
    ```java
    package javaUtilExam;
    
    import java.util.TreeSet;
    
    public class TreeSetExam {
        public static void main(String[] args) {
            TreeSet<Integer> set = new TreeSet<>();
            set.add(10);
            set.add(20);
            set.add(30);
            set.add(40);
            set.add(50);
    
            // ceiling: 지정한 값 이상인 요소 중 가장 작은 값 반환
            System.out.println("ceiling(25): " + set.ceiling(25)); // 30
            System.out.println("ceiling(40): " + set.ceiling(40)); // 40
            System.out.println("ceiling(60): " + set.ceiling(60)); // null (없음)
    
            // floor: 지정한 값 이하인 요소 중 가장 큰 값 반환
            System.out.println("floor(25): " + set.floor(25));     // 20
            System.out.println("floor(10): " + set.floor(10));     // 10
            System.out.println("floor(5): " + set.floor(5));       // null (없음)
    
            // higher: 지정한 값보다 큰 요소 중 가장 작은 값 반환
            System.out.println("higher(25): " + set.higher(25));   // 30
            System.out.println("higher(50): " + set.higher(50));   // null (없음)
    
            // lower: 지정한 값보다 작은 요소 중 가장 큰 값 반환
            System.out.println("lower(25): " + set.lower(25));     // 20
            System.out.println("lower(10): " + set.lower(10));     // null (없음)
    
            // pollFirst: 첫 번째 요소 반환 및 제거
            System.out.println("pollFirst(): " + set.pollFirst()); // 10, 제거됨
            System.out.println("After pollFirst: " + set);         // [20, 30, 40, 50]
    
            // pollLast: 마지막 요소 반환 및 제거
            System.out.println("pollLast(): " + set.pollLast());   // 50, 제거됨
            System.out.println("After pollLast: " + set);          // [20, 30, 40]
        }
    }
    
    ```
