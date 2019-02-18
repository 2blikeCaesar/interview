# Heap

## 1. Heap의 특징

힙의 특징은 아래와 같다.

* 최대값과 최소값을 빠르게 찾기 위한 완전이진트리를 기본으로 한 자료구조다.

* 즉, 우선순위 큐를 위하여 만들어진 자료구조이며 배열을 통해 구현 할 수 있다.

* 부모와 자식간에는 반드시 대소관계가 성립한다.

* 최대힙의 경우 부모는 항상 자식보다 키 값이 크며 최소힙은 부모는 항상 자식보다 키 값이 작다.

* 일종의 반정렬 상태를 유지한다.(느슨한 정렬 상태)

* 힙 트리에서는 중복된 값을 허용한다.

* 구현을 쉽게 하기 위해 배열의 첫번째 인덱스(0)는 사용하지 않는다.


배열을 이용하여 힙을 구현하기 위해서는 아래의 기본적인 것을 만족시켜야 한다.

* 부모 노드 인덱스 = (자식 노드 인덱스 / 2)

* 왼쪽 자식 노드 인덱스 = (부모 노드 인덱스 * 2)

* 오른쪽 자식 노드 인덱스 = (부모 노드 인덱스 * 2) + 1


## 2. Heap 삽입

새로운 값이 Heap에 삽입 되면 아래와 같은 순서가 수행 된다.

* 새로운 노드를 마지막 노드옆에 삽입

* 삽입 된 노드를 부모 노드와 비교하면서 힙의 성질을 만족시키면서 교환한다.


## 3. Heap 삭제

힙에서 삭제란 최대힙일 경우 최대값을, 최소힙일 경우 최소값을 삭제한다.

즉, 루트 노드를 삭제하는 행위를 말한다.

* 루트 노드를 삭제한다. (배열의 인덱스가 1인 값)

* 마지막 인덱스의 값을 루트노드로 이동한다.

* 힙의 성질에 맞게 힙을 재구성한다.


## 4. java code

~~~java
public class Main {

    public static int currentIndex = 0;

    public static int maxHeap[] = new int[11];

//    public static int minHeap[] = new int[4];

    public static final int arr[] = {1, 5, 4, 9, 2, 10, 3, 8, 7, 6};

    public static void main(String args[]) {
        for (int i = 0; i < arr.length; i++) {
            heapifyMax(arr[i]);
        }

        for (int i = 1; i < currentIndex; i++) {
            System.out.print(maxHeap[i] + ", ");
        }

        System.out.println();
        System.out.println("delete " + deleteMax());
        System.out.println("delete " + deleteMax());
        System.out.println("delete " + deleteMax());
        System.out.println();
        for (int i = 1; i < currentIndex; i++) {
            System.out.print(maxHeap[i] + ", ");
        }
    }

    public static int deleteMax() {
        int delete = maxHeap[1];
        maxHeap[1] = maxHeap[currentIndex--];

        for (int i = 1; i * 2 <= currentIndex; ) {
            if (maxHeap[i] > maxHeap[i * 2] && maxHeap[i] > maxHeap[i * 2 + 1]) {
                break;
            } else if (maxHeap[i * 2] > maxHeap[i * 2 + 1]) {
                int tmp = maxHeap[i];
                maxHeap[i] = maxHeap[i * 2];
                maxHeap[i * 2] = tmp;
                i = i * 2;
            } else {
                int tmp = maxHeap[i];
                maxHeap[i] = maxHeap[i * 2 + 1];
                maxHeap[i * 2 + 1] = tmp;
                i = i * 2 + 1;

            }
        }

        return delete;
    }

    public static void heapifyMax (int value) {

        maxHeap[++currentIndex] = value;

        for (int i = currentIndex; i  > 1; i /= 2) {
            if (maxHeap[i/2] < maxHeap[i]) {
                int tmp = maxHeap[i/2];
                maxHeap[i/2] = maxHeap[i];
                maxHeap[i] = tmp;
            }
            else {
                break;
            }
        }
    }

//    public static void heapifyMin (int value) {
//        minHeap[++currentIndex] = value;
//
//        for (int i = currentIndex; i  > 1; i /= 2) {
//            if (minHeap[i/2] > minHeap[i]) {
//                int tmp = minHeap[i/2];
//                minHeap[i/2] = minHeap[i];
//                minHeap[i] = tmp;
//            }
//            else {
//                break;
//            }
//        }
//    }
}
~~~



ㅇ
