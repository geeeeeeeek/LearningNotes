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
### Builder模式

用于替代java bean里面众多的setter方法

```
public class NutritionFacts {
	private final int servings;
	private final int fat;
	private final int sodium;
	
	public static class Builder{
		private int servings;
		private int fat;
		private int sodium;
		public Builder() {}
		
		public Builder servings(int val) {
			servings = val;
			return this;
		}
		
		public Builder fat(int val) {
			fat = val;
			return this;
		}
		
		public Builder sodium(int val) {
			sodium = val;
			return this;
		}
		
		public NutritionFacts build() {
			return new NutritionFacts(this);
		}
	}
	
	private NutritionFacts(Builder builder) {
		servings = builder.servings;
		fat = builder.fat;
		sodium = builder.sodium;
	}
	
	public static void main(String aa[]) {
		NutritionFacts facts = new NutritionFacts.Builder()
				.servings(20)
				.fat(13)
				.sodium(25)
				.build();
	}
}
```
