# Stack And Queue


## 1. stack
선형 자료 구조의 일종
(선형 자료는 원소들을 순차적으로 나열 시킨 형태를 의미하며 리스트 스택 큐 데크 링크드리스트 선형리스트가 존재)

LIFO 구조
(나중에 들어온 원소가 제일 먼저 나감)

시스템 스택에 사용 됨
프로그램간의 호출과 복귀에 따른 수행순서의 경우 스택에 넣고
마지막에 호출 된 것을 처리하고 순차적으로 돌아오게 함.

너비우선탐색의 경우 큐를 사용하지만 깊이우선탐색의 경우 스택을 일반적으로 사용.

## 2. queue
선형 자료 구조의 일종

FIFO 구조
(처음에 들어온 원소가 제일 먼저 나감)

선형 큐
가장 기본적인 큐로 크기가 제한 되어 있으며 빈 공간을 사용하려면 모든 자료를 꺼내거나 자료를 한 칸 씩 옮겨야 한다는 단점이 존재

환형 큐
선형 큐의 문제점을 해결한 방식으로 빈 공간에 추가된 원소를 넣고 원형으로 연결하는 방식

Heap의 경우 완전 이진 트리의 일종으로 우선순위 큐를 위하여 만든 자료 구조이다.

여기서 우선순위 큐란 일반적인 큐와 달리
별도의 우선 순위가 존재하여 들어온 순서와 별개로 우선순위가 높은 원소가 먼저 나가는 형식이다.

우선순위 큐는
시뮬레이션 시스템, 네트워크 트래픽 제어, 운영체지의 작업 스케쥴링 등에 사용 된다.

힙은 완전 이진 트리의 일종이다.
즉 우선순위 큐에서 중요한 우선순위를 빠르게 찾기 위한 자료구조이다.

힙 역시 부모 노드가 자식노드보다 반드시 값이 큰 최대 힙과
그 반대인 부모 노드가 자식노드보다 값이 작은 최소 힙이 존재한다.

힙 트리는 일반적으로 중복 값을 허용한다.







## 구현 예제
### 1. Java 로 구현한 간단한 Stack

~~~java
public class Main {
    public static void main(String args[]) {
        Stack stack = new Stack(5);

        stack.push(5);
        stack.push(4);
        stack.push(3);
        stack.push(2);
        stack.push(1);

        for (int i = 0; i < 5; i++) {
            System.out.println(stack.pop());
        }
    }
}

class Stack {

    Object stack[];
    int index;

    public Stack(int size) {
        this.index = 0;
        stack = new Object[size];
    }

    public void push (Object num) {
        stack[index++] = num;
    }

    public Object pop () {
        return stack[--index];
    }

    public Object peek() {
        return stack[index - 1];
    }

    public boolean isEmpty () {
        return index <= 0;
    }
}
~~~

### 2. Stack으로 Queue 구현

~~~java
public class Main {
    public static void main(String args[]) {
        Stack stack = new Stack(5);

        stack.push(5);
        stack.push(4);
        stack.push(3);
        stack.push(2);
        stack.push(1);

        Stack stack2 = new Stack(5);

        while (!stack.isEmpty()) {
            stack2.push(stack.pop());
        }

        for (int i = 0; i < 5; i++) {
            System.out.println(stack2.pop());
        }
    }
}

class Stack {

    Object stack[];
    int index;

    public Stack(int size) {
        this.index = 0;
        stack = new Object[size];
    }

    public void push (Object num) {
        stack[index++] = num;
    }

    public Object pop () {
        return stack[--index];
    }

    public Object peek() {
        return stack[index - 1];
    }

    public boolean isEmpty () {
        return index <= 0;
    }

}
~~~

### 3. Stack으로 괄호 검사

여는 괄호가 나올 때마다 스택에 저장

닫는 괄호가 나올 때 스택을 pop

이때 만약 형식이 불일치 하다면 에러 발생

~~~java
public class Main {
    private static String successStr1 = "[[{(((({[][]()(){}}))))}]]";
    private static String successStr2 = "{[][]c(a){b}}[d]";

    private static String failStr1 = "[[{(((({[][]((){}}))))}]]";
    private static String failStr2 = "[][]u[]j[]f{}d(a)[(]";

    public static void main(String args[]) throws Exception{
        System.out.println(check(successStr1));
        System.out.println(check(successStr2));
        System.out.println(check(failStr1));
        System.out.println(check(failStr2));
    }

    public static boolean check (String str) {
        Stack stack = new Stack(str.length());

        char charArray[] = str.toCharArray();

        for(int i = 0; i < charArray.length; i++) {
            char ch = charArray[i];
            if (ch == '[' || ch== '{' || ch == '(') {
                stack.push(ch);
            }
            else if (ch == ']' && (char)(stack.pop()) != '[') {
                return false;
            }
            else if (ch == '}' && (char)(stack.pop()) != '{') {
                return false;
            }
            else if (ch == ')' && (char)(stack.pop()) != '(') {
                return false;
            }
        }
        return true;
    }
}

class Stack {

    Object stack[];
    int index;

    public Stack(int size) {
        this.index = 0;
        stack = new Object[size];
    }

    public void push (Object num) {
        stack[index++] = num;
    }

    public Object pop () {
        return stack[--index];
    }

    public Object peek() {
        return stack[index - 1];
    }

    public boolean isEmpty () {
        return index <= 0;
    }

}
~~~




### 4. Queue 구현

~~~java
public class Main {
    public static void main(String args[]) throws Exception{
        Queue queue = new Queue(5);

        queue.enQueue(5);
        queue.enQueue(4);
        queue.enQueue(3);
        queue.enQueue(2);
        queue.enQueue(1);

        while(!queue.isEmpty()) {
            System.out.println(queue.deQueue());
        }
    }
}

class Queue {
    int front;
    int rear;
    Object queue[];

    public Queue(int size) {
        queue = new Object[size];
        front = -1;
        rear = -1;
    }

    public void enQueue(Object obj) throws Exception{
        if(isFull()) {
            throw new Exception("Full");
        }
        queue[++rear] = obj;
    }

    public Object deQueue() throws Exception{
        if(isEmpty()) {
            throw new Exception("Empty");
        }

        Object object = queue[++front];

        if(isEmpty()) {
            front = -1;
            rear = -1;
        }
        return object;
    }

    public Object peek() throws Exception{
        if(isEmpty()) {
            throw new Exception("Empty");
        }
        return queue[front  + 1];
    }

    public boolean isFull() {
        return this.rear == this.queue.length - 1;
    }

    public boolean isEmpty() {
        return rear == front;
    }
}
~~~

d
