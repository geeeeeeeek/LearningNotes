### 单例模式

饿汉式

```
public class Singleton{
    //类加载时就初始化
    private static final Singleton instance = new Singleton();
    
    private Singleton(){}
    public static Singleton getInstance(){
        return instance;
    }
}
```

懒汉式

```
public class Singleton {  
    //静态内部类
    private static class SingletonHolder {  
        private static final Singleton INSTANCE = new Singleton();  
    }  
    private Singleton (){}  
    public static final Singleton getInstance() {  
        return SingletonHolder.INSTANCE; 
    }  
}
```
