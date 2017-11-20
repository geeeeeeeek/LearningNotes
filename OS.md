### java实现生产者消费者模型

首先是阻塞队列的接口

```
public interface IBlockingQueue<T> {

    void put(T data) throws InterruptedException;

    T take() throws InterruptedException;
}
```

使用wait()/notifyAll()实现

```
public class TraditionalBlockingQueue<T> implements IBlockingQueue<T> {
    private int queueSize;
    private final LinkedList<T> list = new LinkedList<T>();
    private final Object lock = new Object();

    public TraditionalBlockingQueue(){
        this(10);
    }
    public TraditionalBlockingQueue(int queueSize) {
        if(queueSize<1){
            throw new IllegalArgumentException("queueSize must be positive number");
        }
        this.queueSize = queueSize;
    }

    @Override
    public void put(T data) throws InterruptedException {

        synchronized (lock){
            while(list.size()>=queueSize) {
                lock.wait();
            }
            list.addLast(data);
            lock.notifyAll();
        }
    }

    @Override
    public T take() throws InterruptedException {

        synchronized(lock){
            while(list.size()<=0) {
                lock.wait();
            }
            T data = list.removeFirst();
            lock.notifyAll();
            return data;
        }
    }
} 
```

问题：为什么在wait()/notify()外面加synchronized同步块？

1. 程序会抛出java.lang.IllegalMonitorStateException  
2. 若不加锁，容易造成竞态条件错乱，例如下面  
```
void put(){
if(size <= 0)
    wait();
    size--;
}
    ...
    
void get(){
if(size > 0)
    size++;
    notify();
}
```

若size加1后，put()方法只执行到wait()之前，那么wait()会一直阻塞下去。
