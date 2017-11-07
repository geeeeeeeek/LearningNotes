# AlgorithmExercise
some algorithm exercise

### 二维数组的查找
在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
 
思路1
 
```
public class Solution {
    public boolean Find(int [][] array,int target) {


        for(int i=0;i<array.length;i++){
            int low=0;
            int high=array[i].length-1;
            while(low<=high){
                int mid=(low+high)/2;
                if(target>array[i][mid])
                    low=mid+1;
                else if(target<array[i][mid])
                    high=mid-1;
                else
                    return true;
            }
        }
        return false;

    }
}
```
思路2：

```
public class Solution {
    public boolean Find(int [][] array,int target) {
        int m = array.length - 1;
        int i = 0;
        while(m >= 0 && i < array[0].length){
            if(array[m][i] > target)
                m--;
            else if(array[m][i] < target)
                i++;
            else
                return true;
        }


        return false;
    }
}
```

### 旋转数组的最小数字
例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。 
 
思路：二分查找的思想
 
```
 public int minNumberInRotateArray(int [] array) {
        int low = 0 ; int high = array.length - 1;   
        while(low < high){
            int mid = low + (high - low) / 2;        
            if(array[mid] > array[high]){
                low = mid + 1;
            }else if(array[mid] == array[high]){
                high = high - 1;
            }else{
                high = mid;
            }   
        }
        return array[low];
    }
```
