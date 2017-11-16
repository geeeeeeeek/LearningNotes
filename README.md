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
### 求二叉树第k层节点个数
递归解法：
 
（1）如果二叉树为空或者k<1返回0
 
（2）如果二叉树不为空并且k==1，返回1
 
（3）如果二叉树不为空且k>1，返回左子树中k-1层的节点个数与右子树k-1层节点个数之和
 
参考代码如下：
```
int GetNodeNumKthLevel(BinaryTreeNode * pRoot, int k)  
{  
    if(pRoot == NULL || k < 1)  
        return 0;  
    if(k == 1)  
        return 1;  
    int numLeft = GetNodeNumKthLevel(pRoot->m_pLeft, k-1); // 左子树中k-1层的节点个数  
    int numRight = GetNodeNumKthLevel(pRoot->m_pRight, k-1); // 右子树中k-1层的节点个数  
    return (numLeft + numRight);  
}
```

### 打印二叉树每层的最右侧结点

思路：利用cur变量记录位置

```
  static   public List<Integer> rightSideView(TreeNode root) {  
        if(root == null){  
            return  new ArrayList<Integer>();  
        }  
        TreeNode currentTreeNode = new TreeNode(0);  
        List<Integer> list = new ArrayList<Integer>();  
        Queue<TreeNode> queue = new LinkedList<TreeNode>();  
        queue.add(root);  
        int cur =0, last =1;  
        while(queue.size() != 0){  
            while(cur < last){  
                currentTreeNode = queue.remove();  
                if(currentTreeNode.left != null){  
                    queue.add(currentTreeNode.left);  
                }  
                if(currentTreeNode.right != null){  
                    queue.add(currentTreeNode.right);  
                }  
                cur++;  
            }  
            list.add(currentTreeNode.val);  
  
            cur =0;  
            last = queue.size();  
        }  
        return  list;  
    } 
```

### 最大连续数组的和

如：[2, -3, 5, 6, -4, 2, -3, 6, 2] 的最大连续数组是[5, 6] 和为11

思路：负的+负的 会更小，正的+正的 会更大

```
int maxSubArray(int A[], int n){
        int sum = Integer.MIN_VALUE;
        int max_sum = Integer.MIN_VALUE;
        for(int i = 0;i < n; i++){
            if(sum > 0){
                sum += A[i];
            }else{
                sum = A[i];
            }
            if(sum > max_sum){
                max_sum = sum;
            }
        }
        return max_sum;
}
```

### 使用数组实现一个栈
```
public class Stack {

    //存数据的数组
    int[] data;

    //栈的最大长度
    private int size;
    //栈顶的位置
    private int top;

    public Stack(int size) {
        this.size = size;
        data = new int[size];
        top = -1;
    }

    public int getSize() {
        return size;
    }

    public int getTop() {
        return top;
    }

    // 判断是否为空栈 
    public boolean isEmpty()     {
        return top == -1;
    }

    // 判断是否为满栈 
    public boolean isFull() {
        return (top+1) == size;
    }

    // 压栈操作 
    public boolean push(int data) {
        if(isFull()) {
            System.out.println("the stack is full!");
            return false;
        } else {
            top++;
            this.data[top] = data;
            return true;
        }
    }


    // 弹栈操作 
    public int pop() throws Exception {
        if(isEmpty()) {
            throw new Exception("the stack is empty!");
        } else {
            return this.data[top--];
        }
    }

    // 获取栈顶的元素,但不弹栈
    public int peek() {
        return this.data[getTop()];
    }

}
```

### 桶排序

身高排队问题；按年龄排序问题等

```
#include <stdio.h>
    int main()
    {
        int a[11],i,j,t;
        for(i=0;i<=10;i++)
            a[i]=0;  //初始化为0

        for(i=1;i<=5;i++)  //循环读入5个数
        {
            scanf("%d",&t);  //把每一个数读到变量t中
            a[t]++;  //进行计数
        }
        for(i=0;i<=10;i++)  //依次判断a[0]~a[10]
            for(j=1;j<=a[i];j++)  //出现了几次就打印几次
                printf("%d ",i);
        getchar();getchar();
        //这里的getchar();用来暂停程序，以便查看程序输出的内容
        //也可以用system("pause");等来代替
        return 0;
    }
```
