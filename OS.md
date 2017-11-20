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
