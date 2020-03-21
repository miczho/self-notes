# Queue

<img src="../Pictures/queue.png" width="400">

First-In-First-Out (FIFO)

Main operations are:
- __enqueue(e)__ adds an element to the back - O(1)
- __dequeue()__ removes and returns the first element - O(1)


Other important operations:
- __size()__ - O(1)
- __isEmpty()__ - O(1)
- __first__ returns (but doesn't remove) first element - O(1)

### ArrayQueue

Presents a fixed size problem.

<details>
	<summary>Array Implementation</summary>

```java
public class ArrayQueue<E> implements Queue<E> {
  // instance variables
  /** Default array capacity. */
  public static final int CAPACITY = 1000;      // default array capacity

  /** Generic array used for storage of queue elements. */
  private E[] data;                             // generic array used for storage

  /** Index of the top element of the queue in the array. */
  private int f = 0;                            // index of the front element

  /** Current number of elements in the queue. */
  private int sz = 0;                           // current number of elements

  // constructors
  /** Constructs an empty queue using the default array capacity. */
  public ArrayQueue() {this(CAPACITY);}         // constructs queue with default capacity

  /**
   * Constructs and empty queue with the given array capacity.
   * @param capacity length of the underlying array
   */
  @SuppressWarnings({"unchecked"})
  public ArrayQueue(int capacity) {             // constructs queue with given capacity
    data = (E[]) new Object[capacity];          // safe cast; compiler may give warning
  }

  // methods
  /**
   * Returns the number of elements in the queue.
   * @return number of elements in the queue
   */
  @Override
  public int size() { return sz; }

  /** Tests whether the queue is empty. */
  @Override
  public boolean isEmpty() { return (sz == 0); }

  /**
   * Inserts an element at the rear of the queue.
   * This method runs in O(1) time.
   * @param e   new element to be inserted
   * @throws IllegalStateException if the array storing the elements is full
   */
  @Override
  public void enqueue(E e) throws IllegalStateException {
    if (sz == data.length) throw new IllegalStateException("Queue is full");
    int avail = (f + sz) % data.length;   // use modular arithmetic
    data[avail] = e;
    sz++;
  }

  /**
   * Returns, but does not remove, the first element of the queue.
   * @return the first element of the queue (or null if empty)
   */
  @Override
  public E first() {
    if (isEmpty()) return null;
    return data[f];
  }

  /**
   * Removes and returns the first element of the queue.
   * @return element removed (or null if empty)
   */
  @Override
  public E dequeue() {
    if (isEmpty()) return null;
    E answer = data[f];
    data[f] = null;                             // dereference to help garbage collection
    f = (f + 1) % data.length;
    sz--;
    return answer;
  }

  /**
   * Returns a string representation of the queue as a list of elements.
   * This method runs in O(n) time, where n is the size of the queue.
   * @return textual representation of the queue.
   */
  public String toString() {
    StringBuilder sb = new StringBuilder("(");
    int k = f;
    for (int j=0; j < sz; j++) {
      if (j > 0)
        sb.append(", ");
      sb.append(data[k]);
      k = (k + 1) % data.length;
    }
    sb.append(")");
    return sb.toString();
  }
}
```

</details>

### LinkedQueue

Doesn't have a size problem.

<details>
	<summary>Linked List Implementation</summary>

```java
public class LinkedQueue<E> implements Queue<E> {

  /** The primary storage for elements of the queue */
  private SinglyLinkedList<E> list = new SinglyLinkedList<>();   // an empty  list

  /** Constructs an initially empty queue. */
  public LinkedQueue() { }                  // new queue relies on the initially empty list

  /**
   * Returns the number of elements in the queue.
   * @return number of elements in the queue
   */
  @Override
  public int size() { return list.size(); }

  /**
   * Tests whether the queue is empty.
   * @return true if the queue is empty, false otherwise
   */
  @Override
  public boolean isEmpty() { return list.isEmpty(); }

  /**
   * Inserts an element at the rear of the queue.
   * @param element  the element to be inserted
   */
  @Override
  public void enqueue(E element) { list.addLast(element); }

  /**
   * Returns, but does not remove, the first element of the queue.
   * @return the first element of the queue (or null if empty)
   */
  @Override
  public E first() { return list.first(); }

  /**
   * Removes and returns the first element of the queue.
   * @return element removed (or null if empty)
   */
  @Override
  public E dequeue() { return list.removeFirst(); }

  /** Produces a string representation of the contents of the queue.
   *  (from front to back). This exists for debugging purposes only.
   */
  public String toString() {
    return list.toString();
  }
}
```

</details>

## Double-Ended Queue (Deque)

![](../Pictures/deque.png)

Can add or remove from both ends.

Main operations are:
- __addFirst(e)__
- __addLast(e)__
- __removeFirst()__
- __removeLast()__