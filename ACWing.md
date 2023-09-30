# ACWing周赛

## 第 33 场周赛

### AcWing 4206. 判断数字

> 给定一个整数 *n*，请你统计其各位数字中 4 和 7
>
>  的出现次数。
>
> 如果 4
>
>  的出现次数加上 7 的出现次数恰好等于 4 或 7
>
> ，则输出 `YES`，否则输出 `NO`。
>
> 例如，当 *n*=40047
>
>  时，4 出现了 2 次，7 出现了 1 次，2+1=3，既不是 4 也不是 7，因此，输出 `NO`；当 *n*=7747774 时，4 出现了 2 次，7 出现了 5 次，2+5=7，因此，输出 `YES`。
>
> #### 输入样例1：
>
> ```
> 40047
> ```
>
> #### 输出样例1：
>
> ```
> NO
> ```
>
> #### 输入样例2：
>
> ```
> 7747774
> ```
>
> #### 输出样例2：
>
> ```
> YES
> ```

```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        long num= sc.nextLong();
        int acount=0;
        int bcount=0;
        while(num>0){
            if(num%10==4){
                acount++;
                num/=10;
            }
            else if(num%10==7){
                bcount++;
                num/=10;
            }
            else{
                num/=10;
            }
        }
        if(acount+bcount==4||acount+bcount==7){
            System.out.println("YES");
        }
        else{
            System.out.println("NO");
        }
    }
}

```

### AcWing 4207. 最长合法括号子序列

> 一个合法的括号序列满足以下条件：
>
> 1. 序列`()`被认为是合法的。
> 2. 如果序列`X`与`Y`是合法的，则`XY`也被认为是合法的。
> 3. 如果序列`X`是合法的，则`(X)`也是合法的。
>
> 例如，`()`，`()()`，`(())`这些都是合法的。
>
> 现在，给定一个由 `(` 和 `)` 组成的字符串。
>
> 请你求出其中的最长合法括号**子序列**的长度。
>
> 注意，子序列不一定连续。
>
> #### 输入样例1：
>
> ```
> (()))(
> ```
>
> #### 输出样例1：
>
> ```
> 4
> ```
>
> #### 输入样例2：
>
> ```
> ()()(()(((
> ```
>
> #### 输出样例2：
>
> ```
> 6
> ```

```java
import java.util.Deque;
import java.util.Scanner;
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack<Character> s=new Stack<>();
        Scanner sc=new Scanner(System.in);
        String ss=new String();
        ss=sc.next();
        int a_count=0;
        int b_count=0;
        int ans=0;
        for(int i=0;i<ss.length();i++){
            if(ss.charAt(i)=='('){
                a_count++;
            }
            else{
                if(a_count>0){
                    a_count--;
                    ans+=2;
                }
            }
        }
        System.out.println(ans);
    }
}
```

## 第 34 场周赛 

### AcWing 4209. 三元组

> #### 格式
>
> 如果能够同时满足三个条件，则输出 `YES`，否则输出 `NO`。
>
> #### 数据范围
>
> 前三个测试点满足 1≤*n*≤10
>
> 。
>  所有测试点满足 1≤*n*≤100，−100≤*x**i*,*y**i*,*z**i*≤100
>
> 。
>
> #### 输入样例1：
>
> ```
> 4
> 3 -1 7
> -5 2 -4
> 0 -2 -1
> 2 1 -2
> ```
>
> #### 输出样例1：
>
> ```
> YES
> ```
>
> #### 输入样例2：
>
> ```
> 3
> 4 1 7
> -2 4 -1
> 1 -5 -3
> ```
>
> #### 输出样例2：
>
> ```
> NO
> ```

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int num=sc.nextInt();
        int[][] array=new int[num][3];
        for(int i=0;i<num;i++){
            for(int j=0;j<3;j++){
                array[i][j]=sc.nextInt();
            }
        }
        for(int i=0;i<3;i++){
            int temp=0;
            for(int j=0;j<num;j++){
                temp+=array[j][i];
            }
            if(temp!=0) {
                System.out.println("NO");
                return;
            }
        }
        System.out.println("YES");
    }
}

```

### AcWing 4210. 数字

> 给定一个大于 2 的十进制正整数 *A*
>
> 。
>
> 该数字在 2∼*A*−1
>
>  进制表示下的各位数字之和均可以求出。
>
> 例如，数字 123
>
>  在 16 进制表示下，共有 2 位：第 1 位是 7，第二位是 11，各位数字之和为 18
>
> 。
>
> 现在，请你将 *A*
>
>  在 2∼*A*−1 进制表示下的各位数字之和全部相加，并将得到的结果除以 *A*−2
>
> ，最终结果以最简分数形式输出。
>
> #### 输入格式
>
> 一个十进制正整数 *A*
>
> 。
>
> #### 输出格式
>
> 输出格式为 `X/Y`，其中 *X*
>
>  表示输出答案的分子，*Y*
>
>  表示输出答案的分母。
>
> #### 数据范围
>
> 前三个测试点满足 3≤*A*≤10
>
> 
>  所有测试点满足 3≤*A*≤1000
>
> 
>
> #### 输入样例1：
>
> ```
> 5
> ```
>
> #### 输出样例1：
>
> ```
> 7/3
> ```
>
> #### 输入样例2：
>
> ```
> 3
> ```
>
> #### 输出样例2：
>
> ```
> 2/1
> ```

```java

import java.util.List;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int[][] array=new int[10010][10010];
        int n= sc.nextInt();
        int num= n;
        for(int i=2;i<=num-1;i++){
            int temp=0;
            int n1=num;
            do {
                array[i][temp++]=n1%i;
                n1=n1/i;
            }while(n1!=0);
        }
        int ans=0;
        for(int i=2;i<=num-1;i++){
            for(int j=0;j<array[i].length;j++){
                ans+=array[i][j];
            }
        }
        int a=ans,b=n-2;
        int g=1;
        for(int i=1;i<=n-2;i++){
            if(a%i==0&&b%i==0){
               g=i;
            }
        }
        if(ans%(n-2)==0) System.out.println(ans/(n-2)+"/"+1);
        else System.out.println((a/g)+"/"+(b/g));
    }
}

```

## 第 35 场周赛

### 4212. 字符串比较            

> 给定两个长度相等的**由大小写英文字母构成**的字符串 *A* 和 *B*
>
> 请你按照字典顺序对这两个字符串进行比较。
>
> 注意，在进行比较时，字母的**大小写无关紧要**，即大写字母被认为等同于相应的小写字母。
>
> #### 输入格式
>
> 第一行，字符串 *A*
>
> 第二行，字符串 *B*
>
> #### 输出格式
>
> 如果 *A*>*B*，则输出 1，如果 *A*<*B*，则输出 −1，如果 *A*=*B*，则输出 0。
>
> #### 数据范围
>
> 所有测试点满足，1≤|*A*|,|*B*|≤100
>
> #### 输入样例1：
>
> ```
> aaaa
> aaaA
> ```
>
> #### 输出样例1：
>
> ```
> 0
> ```
>
> #### 输入样例2：
>
> ```
> abs
> Abz
> ```
>
> #### 输出样例2：
>
> ```
> -1
> ```
>
> #### 输入样例3：
>
> ```
> abcdefg
> AbCdEfF
> ```
>
> #### 输出样例3：
>
> ```
> 1
> ```

```java
import java.util.Locale;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String a=sc.next();
        String b=sc.next();
        if(a.equalsIgnoreCase(b)) {
            System.out.println(0);
            return;
        }
        else{
            for(int i=0;i<a.length();i++){
                char temp1=a.charAt(i);
                if(a.charAt(i)>=97&&a.charAt(i)<=100){
                    temp1=(char)(temp1-32);
                }
                char temp2=b.charAt(i);
                if(b.charAt(i)>=97&&b.charAt(i)<=100){
                    temp2=(char) (temp2-32);
                }
                if(temp1>temp2) {System.out.println(1);return;}
                else if(temp1<temp2) {System.out.println(-1);return;}
            }
            System.out.println(0);
        }
    }
}

```

### 4213. 最小结果

> 有四个整数 *a*,*b*,*c*,*d*
>
> 有三个操作符 *o**p*1,*o**p*2,*o**p*3，每个操作符要么是 `*`（表示乘法），要么是 `+`（表示加法）。
>
> 现在，我们要进行如下操作：
>
> 1. 从现有整数中选出两个，按 *o**p*1 进行运算，得到结果。将选出的两个整数舍弃，并将结果保留。此时我们还剩下三个整数。
> 2. 从现有整数中选出两个，按 *o**p*2进行运算，得到结果。将选出的两个整数舍弃，并将结果保留。此时我们还剩下两个整数。
> 3. 从现有整数中选出两个，按 *o**p*3
>
> 1.  进行运算，得到结果。将选出的两个整数舍弃，并将结果保留。此时我们只剩下一个整数。
>
> 我们希望，最后剩下的一个整数尽可能小。
>
> #### 输入格式
>
> 第一行包含四个整数 *a*,*b*,*c*,*d*
>
> 第二行包含三个操作符 *o**p*1,*o**p*2,*o**p*3，每个操作符要么是 `*`，要么是 `+`。
>
> #### 输出格式
>
> 输出最后剩下的一个整数的最小可能值。
>
> #### 数据范围
>
> 所有测试点满足 0≤*a*,*b*,*c*,*d*≤1000
>
> #### 输入样例1：
>
> ```
> 1 1 1 1
> + + *
> ```
>
> #### 输出样例1：
>
> ```
> 3
> ```
>
> #### 输入样例2：
>
> ```
> 2 2 2 2
> * * +
> ```
>
> #### 输出样例2：
>
> ```
> 8
> ```
>
> #### 输入样例3：
>
> ```
> 1 2 3 4
> * + +
> ```
>
> #### 输出样例3：
>
> ```
> 9
> ```

```java
package 习题;

import java.util.ArrayList;
import java.util.List;
import java.util.Arrays;
import java.util.Scanner;

public class acw4213_test {
    static List<Long> array=new ArrayList<>();
    static char[] array1=new char[5];
    static long ans=Long.MAX_VALUE;//由于四位数相乘，最大值为1e12，因此可以用Long类型来存储
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        for(int i=0;i<4;i++) array.add(sc.nextLong());//输入数据
        for(int i=0;i<3;i++) array1[i]=sc.next().charAt(0);//输入运算符
        dfs(array,0);//DFS爆搜
        System.out.println(ans);
    }
    private static void dfs(List<Long> array,int count){
        if(array.size()==1) {//如果集合中只有1个值就与其他值进行比较，寻找最小值
            ans=Math.min(ans,array.get(0));
        }else{
            for(int i=0;i<array.size();i++){//寻找第一个值
                for(int j=i+1;j<array.size();j++){//寻找第二个值
                    List<Long> array2=new ArrayList<>();//定义一个新的集合
                    for(int m=0;m<array.size();m++){
                        if(m!=i&&m!=j){//将剩余值添加到新集合中
                            array2.add(array.get(m));
                        }
                    }
                    //如果当前字符是*，就进行乘法运算，将运算结果放进新的集合中
                    if(array1[count]=='*') array2.add(array.get(i)*array.get(j));
                    else array2.add(array.get(i)+array.get(j));
                    dfs(array2,count+1);//对新集合进行DFSbaosou
                }
            }
        }
    }
}
```

## 第 36 场周赛  

### AcWing 4215. 处理字符串

> 给定一个由大小写字母构成的字符串，请你对该字符串进行如下处理：
>
> - 将所有大写字母替换为相应的小写字母。
> - 删除其中的所有元音字母。
> - 在每个辅音字母前面插入一个 `.`。
>
> 字母 `a`，`o`，`y`，`e`，`u`，`i` 为元音字母，其余字母均为辅音字母。
>
> 注意，`y` 其实是半元音字母，在本题中规定其为元音字母。
>
> #### 输入格式
>
> 一个由大小写字母构成的字符串。
>
> #### 输出格式
>
> 输出处理后的字符串。
>
> 保证处理后的字符串不为空。
>
> #### 数据范围
>
> 所有测试点满足，字符串长度范围 [1,100]
>
> #### 输入样例1：
>
> ```
> tour
> ```
>
> #### 输出样例1：
>
> ```
> .t.r
> ```
>
> #### 输入样例2：
>
> ```
> aBAcAba
> ```
>
> #### 输出样例2：
>
> ```
> .b.c.b
> ```

```java
package 习题1;

import java.util.Arrays;
import java.util.Locale;
import java.util.Scanner;

public class acw4215_test {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String s1=sc.next();
        String s2=s1.toLowerCase();
        StringBuilder s3=new StringBuilder();
        int temp=0;
        for(int i=0;i<s2.length();i++){
            if(!(s2.charAt(i)=='a'||s2.charAt(i)=='e'||s2.charAt(i)=='i'||s2.charAt(i)=='o'||s2.charAt(i)=='u'||s2.charAt(i)=='y')){
                s3.append('.').append(s2.charAt(i));
            }
        }
        System.out.println(s3);
    }
}
```

1. String对象的toLowerCase可以将字符串里面的大写字母转换成小写字母
2. 对字符串进行拼接操作时尽量使用StringBuilder类

## 第 37 场周赛 

### 4296. 合适数对  

> 给定三个正整数 *n*,*a*,*b*，请你找到两个**非负整数***x*,*y*，使得 *a**x*+*b**y*=*n* 成立。
>
> #### 输入格式
>
> 第一行包含整数 *n*。第二行包含整数 *a*。第三行包含整数 *b*。
>
> #### 输出格式
>
> 如果不存在符合条件的 *x*,*y*，则输出一行 `NO` 即可。
>
> 否则，第一行输出 `YES`，第二行输出                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          *x*,*y*。
>
> 如果方案不唯一，则输出 *x*最小的方案。
>
> #### 数据范围
>
> 所有测试点满足 1≤*n*,*a*,*b*≤1000
>
> #### 输入样例1：
>
> ```
> 7
> 2
> 3
> ```
>
> #### 输出样例1：
>
> ```
> YES
> 2 1
> ```
>
> #### 输入样例2：
>
> ```
> 100
> 25
> 10
> ```
>
> #### 输出样例2：
>
> ```
> YES
> 0 10
> ```
>
> #### 输入样例3：
>
> ```
> 15
> 4
> 8
> ```
>
> #### 输出样例3：
>
> ```
> NO
> ```

> 需要注意的是 

```java
package 习题1;

import java.util.Scanner;

public class acw4296_test {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int a= sc.nextInt();
        int b= sc.nextInt();
        int temp=0;
        int x=0,y=0;
        int t=0;
        boolean flag=false;
        while(true){
            if((n-t*a)%b==0){
                y=n/b;
                x=0;
                break;
            }else{
                t++;
                temp=t*a;
                if((n-temp)%b==0&&(n-temp)>0){
                    x=temp/a;
                    y=(n-temp)/b;
                    break;
                }
                if(temp>=n){
                    if(temp>n) {
                        flag=true;
                        break;
                    }
                    if(temp%a==0){
                        x=temp/a;
                        y=0;
                    }
                    break;
                }
            }
        }
        if(flag) System.out.println("NO");
        else {
            System.out.println("YES");
            System.out.println(x+" "+y);
        }
    }
}
```

## 第 38 场周赛 

### 4299. 删点

> 在一个二维平面上有 nn 个点，其中没有任何一个点位于 yy 轴上。
>
> 请你判断这些点中是否存在一点满足，删除该点后，剩余的所有点都在 yy 轴的同一侧。
>
> #### 输入格式
>
> 第一行包含整数 nn。
>
> 接下来 nn 行，每行包含两个整数 x,yx,y，表示其中一个点的横纵坐标。
>
> 点的位置两两不重合。
>
> #### 输出格式
>
> 如果存在满足要求的点，则输出 `Yes`，否则输出 `No`。
>
> #### 数据范围
>
> 前三个测试点满足 2≤n≤102≤n≤10。
> 所有测试点满足 2≤n≤1002≤n≤100，|x|,|y|≤100|x|,|y|≤100，|x|≠0|x|≠0。
>
> #### 输入样例1：
>
> ```
> 3
> 1 1
> -1 -1
> 2 -1
> ```
>
> #### 输出样例1：
>
> ```
> Yes
> ```
>
> #### 输入样例2：
>
> ```
> 4
> 1 1
> 2 2
> -1 1
> -2 2
> ```
>
> #### 输出样例2：
>
> ```
> No
> ```
>
> #### 输入样例3：
>
> ```
> 3
> 1 2
> 2 1
> 4 60
> ```
>
> #### 输出样例3：
>
> ```
> Yes
> ```

```java
package 习题1;
import java.util.*;
public class acw38_test1 {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int ans1=0;
        int ans2=0;
        for(int i=0;i<n;i++){
            int x=sc.nextInt();
            int y=sc.nextInt();
            if(x>0) ans1++;
            else ans2++;
        }
        if(ans1==1||ans2==1||ans1==0||ans2==0) System.out.println("Yes");
        else System.out.println("No");
    }
}
```

### 4300. 两种操作

> 给定一个正整数 nn，我们希望你可以通过一系列的操作，将其变为另一个正整数 mm。
>
> 操作共分两种：
>
> 1. 将当前的数乘以 22。
> 2. 将当前的数减去 11。
>
> 要求，在变换过程中，**数字始终为正**。
>
> 请你计算，所需要的最少操作次数。
>
> #### 输入格式
>
> 一行，两个不同的正整数 nn 和 mm。
>
> #### 输出格式
>
> 一个整数，表示所需的最少操作次数。
>
> #### 数据范围
>
> 前 66 个测试点满足 1≤n,m≤101≤n,m≤10。
> 所有测试点满足 1≤n,m≤100001≤n,m≤10000。
>
> #### 输入样例1：
>
> ```
> 4 6
> ```
>
> #### 输出样例1：
>
> ```
> 2
> ```
>
> #### 输入样例2：
>
> ```
> 10 1
> ```
>
> #### 输出样例2：
>
> ```
> 9
> ```

```java
package 习题1;
import java.util.*;
public class acw38_test2 {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int m=sc.nextInt();
        int ans=0;
        while(m!=n){
            if(m>n&&m%2==0){
                m/=2;
                ans++;
            }else{
                m+=1;
                ans++;
            }
        }
        System.out.println(ans);
    }
}
```

## 第44场周赛

### 4317. 不同正整数的个数            

> 给定 *n*
>
>  个**非负**整数 *a*1,*a*2,…,*a**n*。
>
> 请你计算其中共有多少个**不同**的**正整数**。
>
> #### 输入格式
>
> 第一行包含整数 *n*
>
> 第二行包含 *n*个非负整数 *a*1,*a*2,…,*a**n*。
>
> 保证至少存在一个正整数。
>
> #### 输出格式
>
> 一个整数，表示其中不同正整数的数量。
>
> #### 数据范围
>
> 前三个测试点满足 1≤*n*≤5。所有测试点满足 1≤*n*≤100，0≤*a**i*≤600
>
> #### 输入样例1：
>
> ```
> 4
> 1 3 3 2
> ```
>
> #### 输出样例1：
>
> ```
> 3
> ```
>
> #### 输入样例2：
>
> ```
> 3
> 1 1 1
> ```
>
> #### 输出样例2：
>
> ```
> 1
> ```
>
> #### 输入样例3：
>
> ```
> 4
> 42 0 0 42
> ```
>
> #### 输出样例3：
>
> ```
> 1
> ```

```java
import java.util.*;
import java.io.*;
public class Main {
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        Set<Integer> s=new HashSet<>();
        int n=sc.nextInt();
        for(int i=0;i<n;i++){
            int temp=sc.nextInt();
            if(temp>0) s.add(temp);
        }
        System.out.println(s.size());
    }
}
```

### 4318. 最短路径            

> 有一个智能机器人，我们可以通过给它发送移动指令来控制它在一个方格矩阵地图中进行移动。
>
> 移动指令共有以下四种：
>
> - `U`，向上移动一格距离。
> - `D`，向下移动一格距离。
> - `L`，向左移动一格距离。
> - `R`，向右移动一格距离。
>
> 矩阵地图可以无限大，矩阵地图中的方格可以是空格也可以是陷阱。
>
> 机器人移动至空格则安然无恙，移动至陷阱则被摧毁。
>
> 现在，机器人的移动指令已经全部设定完毕。
>
> 请问，是否可以构造一个合适的矩阵地图，并选择地图中的两个不同空格位置作为起点和终点，使得：
>
> 1. 机器人能够从起点开始，按照设定好的一系列移动指令进行移动，最终安全抵达终点。
> 2. 机器人的实际移动路径是起点到终点的最短（安全）路径（之一）。
>
> #### 输入格式
>
> 一行，一个由大写字母 `U`、`D`、`L`、`R` 构成的字符串，表示设定完毕的机器人的移动指令。
>
> #### 输出格式
>
> 一行，如果可以构造出合适的地图，则输出 `YES`，否则输出 `NO`。
>
> #### 数据范围
>
> 前三个测试点满足，1≤
>
>  输入字符串长度 ≤10。
>  所有测试点满足，1≤ 输入字符串长度 ≤100。
>
> #### 输入样例1：
>
> ```
> LLUUUR
> ```
>
> #### 输出样例1：
>
> ```
> YES
> ```
>
> #### 输入样例2：
>
> ```
> RRUULLDD
> ```
>
> #### 输出样例2：
>
> ```
> NO
> ```

```java
import java.util.*;
import java.io.*;
public class Main {
    public static void main(String[] args){
        Scanner sc=new Scanner(System.in);
        boolean[][] flag=new boolean[210][210];
        int x=105,y=105;
        int[] dx=new int[]{0,1,0,-1},dy=new int[]{1,0,-1,0};
        String s=sc.next();
        char[] s1=s.toCharArray();
        HashMap<Character,Integer> h=new HashMap<>(){{
            put('R',0);
            put('D',1);
            put('L',2);
            put('U',3);
        }};
        flag[x][y]=true;
        boolean ans=true;
        for(char c:s1){
            int t=h.get(c);
            x+=dx[t];
            y+=dy[t];
            if(flag[x][y]) ans=false;
            for(int i=0;i<4;i++){
                if(i!=(t^2)&&flag[x+dx[i]][y+dy[i]]){
                    ans=false;
                }
            }
            flag[x][y]=true;
        }
        if(ans) System.out.println("YES");
        else System.out.println("NO");
    }
}
```

- 最短路径
  - 1. 保证之前走过的路不会再走第二遍
    2. 保证走过的节点之间不会有相邻点



## 每日一题

### [1282. 用户分组](https://leetcode.cn/problems/group-the-people-given-the-group-size-they-belong-to/)

> 有 n 个人被分成数量未知的组。每个人都被标记为一个从 0 到 n - 1 的唯一ID 。
>
> 给定一个整数数组 groupSizes ，其中 groupSizes[i] 是第 i 个人所在的组的大小。例如，如果 groupSizes[1] = 3 ，则第 1 个人必须位于大小为 3 的组中。
>
> 返回一个组列表，使每个人 i 都在一个大小为 groupSizes[i] 的组中。
>
> 每个人应该 恰好只 出现在 一个组 中，并且每个人必须在一个组中。如果有多个答案，返回其中 任何 一个。可以 保证 给定输入 至少有一个 有效的解。
>
>  
>
> 示例 1：
>
> 输入：groupSizes = [3,3,3,3,3,1,3]
> 输出：[[5],[0,1,2],[3,4,6]]
> 解释：
> 第一组是 [5]，大小为 1，groupSizes[5] = 1。
> 第二组是 [0,1,2]，大小为 3，groupSizes[0] = groupSizes[1] = groupSizes[2] = 3。
> 第三组是 [3,4,6]，大小为 3，groupSizes[3] = groupSizes[4] = groupSizes[6] = 3。 
> 其他可能的解决方案有 [[2,1,6],[5],[0,4,3]] 和 [[5],[0,6,2],[4,3,1]]。
> 示例 2：
>
> 输入：groupSizes = [2,1,3,3,3,2]
> 输出：[[1],[0,5],[2,3,4]]
>
>
> 提示：
>
> groupSizes.length == n
> 1 <= n <= 500
> 1 <= groupSizes[i] <= n
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/group-the-people-given-the-group-size-they-belong-to
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class Solution {
    public List<List<Integer>> groupThePeople(int[] groupSizes) {
        int n = groupSizes.length;
        HashMap<Integer, List<Integer>> hashMap = new HashMap<>();
        for (int i = 0; i < n; i++) {
            hashMap.computeIfAbsent(groupSizes[i], key -> new ArrayList<>()).add(i);
        }

        List<List<Integer>> ans=new ArrayList<>();
        for (int i : hashMap.keySet()) {
            List<Integer> temp=hashMap.get(i);
            for(int j=0;j<temp.size();j+=i){
                List<Integer> temp_ans=new ArrayList<>();
                for(int k=j;k<j+i;k++){
                    temp_ans.add(temp.get(k));
                }
                ans.add(temp_ans);
            }
        }

        return ans;
    }
}
```

### [768. 最多能完成排序的块 II](https://leetcode.cn/problems/max-chunks-to-make-sorted-ii/)

> 这个问题和“最多能完成排序的块”相似，但给定数组中的元素可以重复，输入数组最大长度为2000，其中的元素最大为10**8。
>
> arr是一个可能包含重复元素的整数数组，我们将这个数组分割成几个“块”，并将这些块分别进行排序。之后再连接起来，使得连接的结果和按升序排序后的原数组相同。
>
> 我们最多能将数组分成多少块？
>
> 示例 1:
>
> 输入: arr = [5,4,3,2,1]
> 输出: 1
> 解释:
> 将数组分成2块或者更多块，都无法得到所需的结果。
> 例如，分成 [5, 4], [3, 2, 1] 的结果是 [4, 5, 1, 2, 3]，这不是有序的数组。 
> 示例 2:
>
> 输入: arr = [2,1,3,4,4]
> 输出: 4
> 解释:
> 我们可以把它分成两块，例如 [2, 1], [3, 4, 4]。
> 然而，分成 [2, 1], [3], [4], [4] 可以得到最多的块数。 
> 注意:
>
> arr的长度在[1, 2000]之间。
> arr[i]的大小在[0, 10**8]之间。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/max-chunks-to-make-sorted-ii
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class Solution {
    public int maxChunksToSorted(int[] arr) {
        Deque<Integer> deque=new ArrayDeque<>();
        for(int i:arr){
            while (!deque.isEmpty()&&deque.peek()>i){
                deque.pop();
            }
            deque.push(i);
        }
        return deque.size();
    }
}
```

### \4405. 统计子矩阵

> 给定一个 N×MN×M 的矩阵 AA，请你统计有多少个子矩阵 (最小 1×11×1，最大 N×MN×M) 满足子矩阵中所有数的和不超过给定的整数 KK?
>
> #### 输入格式
>
> 第一行包含三个整数 N,MN,M 和 KK。
>
> 之后 NN 行每行包含 MM 个整数，代表矩阵 AA。
>
> #### 输出格式
>
> 一个整数代表答案。
>
> #### 数据范围
>
> 对于 30%30% 的数据，N,M≤20N,M≤20，
> 对于 70%70% 的数据，N,M≤100N,M≤100，
> 对于 100%100% 的数据，1≤N,M≤500;0≤Aij≤1000;1≤K≤2.5×1081≤N,M≤500;0≤Aij≤1000;1≤K≤2.5×108。
>
> #### 输入样例：
>
> ```
> 3 4 10
> 1 2 3 4
> 5 6 7 8
> 9 10 11 12
> ```
>
> #### 输出样例：
>
> ```
> 19
> ```
>
> #### 样例解释
>
> 满足条件的子矩阵一共有 1919，包含：
>
> - 大小为 1×11×1 的有 1010 个。
> - 大小为 1×21×2 的有 33 个。
> - 大小为 1×31×3 的有 22 个。
> - 大小为 1×41×4 的有 11 个。
> - 大小为 2×12×1 的有 33 个。

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N = 100010;
    static int n, m, k;
    static int[] a;
    static int[] b;
    static int[][] pre_sum;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        str = br.readLine().split(" ");
        n = Integer.parseInt(str[0]);
        m = Integer.parseInt(str[1]);
        k = Integer.parseInt(str[2]);
        pre_sum = new int[n + 1][m + 1];
        for (int i = 1; i <= n; i++) {
            str = br.readLine().split(" ");
            for (int j = 1; j <= m; j++) {
                pre_sum[i][j] = Integer.parseInt(str[j - 1]) + pre_sum[i - 1][j] + pre_sum[i][j - 1] - pre_sum[i - 1][j - 1];
            }
        }

        long ans = 0;
        for (int i = 1; i <= n; i++) {
            for (int j = i; j <= n; j++) {
                int l = 1, r = 1;
                while (r <= m) {
                    while (l <= r && !check(i, l, j, r)) {
                        l++;
                    }
                    ans += (long) r - l + 1;
                    r++;
                }
            }
        }

        bw.write(ans + "");

        bw.flush();
        bw.close();
        br.close();
    }

    public static boolean check(int x1, int y1, int x2, int y2) {
        return pre_sum[x2][y2] - pre_sum[x1 - 1][y2] - pre_sum[x2][y1 - 1] + pre_sum[x1 - 1][y1 - 1] <= k;
    }

}
```

1. 枚举上下边界，然后寻找左右边界，找到不满足情况的右边界，然后r-l+1，就能找到列数

### [641. 设计循环双端队列](https://leetcode.cn/problems/design-circular-deque/)

> 设计实现双端队列。
>
> 实现 MyCircularDeque 类:
>
> MyCircularDeque(int k) ：构造函数,双端队列最大为 k 。
> boolean insertFront()：将一个元素添加到双端队列头部。 如果操作成功返回 true ，否则返回 false 。
> boolean insertLast() ：将一个元素添加到双端队列尾部。如果操作成功返回 true ，否则返回 false 。
> boolean deleteFront() ：从双端队列头部删除一个元素。 如果操作成功返回 true ，否则返回 false 。
> boolean deleteLast() ：从双端队列尾部删除一个元素。如果操作成功返回 true ，否则返回 false 。
> int getFront() )：从双端队列头部获得一个元素。如果双端队列为空，返回 -1 。
> int getRear() ：获得双端队列的最后一个元素。 如果双端队列为空，返回 -1 。
> boolean isEmpty() ：若双端队列为空，则返回 true ，否则返回 false  。
> boolean isFull() ：若双端队列满了，则返回 true ，否则返回 false 。
>
>
> 示例 1：
>
> 输入
> ["MyCircularDeque", "insertLast", "insertLast", "insertFront", "insertFront", "getRear", "isFull", "deleteLast", "insertFront", "getFront"]
> [[3], [1], [2], [3], [4], [], [], [], [4], []]
> 输出
> [null, true, true, true, false, 2, true, true, true, 4]
>
> 解释
> MyCircularDeque circularDeque = new MycircularDeque(3); // 设置容量大小为3
> circularDeque.insertLast(1);			        // 返回 true
> circularDeque.insertLast(2);			        // 返回 true
> circularDeque.insertFront(3);			        // 返回 true
> circularDeque.insertFront(4);			        // 已经满了，返回 false
> circularDeque.getRear();  				// 返回 2
> circularDeque.isFull();				        // 返回 true
> circularDeque.deleteLast();			        // 返回 true
> circularDeque.insertFront(4);			        // 返回 true
> circularDeque.getFront();				// 返回 4
>
>  
>
> 提示：
>
> 1 <= k <= 1000
> 0 <= value <= 1000
> insertFront, insertLast, deleteFront, deleteLast, getFront, getRear, isEmpty, isFull  调用次数不大于 2000 次
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/design-circular-deque
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class MyCircularDeque {
    int[] array;
    int h,t,k;
    public MyCircularDeque(int k) {
        array=new int[k+1];
        h=0;t=0;
        this.k=k;
    }

    private int get(int x){
        return (x+array.length)%array.length;
    }

    public boolean insertFront(int value) {
        if(isFull()) return false;
        h=get(h-1);
        array[h]=value;
        return true;
    }

    public boolean insertLast(int value) {
        if(isFull()) return false;
        array[t]=value;
        t=get(t+1);
        return true;
    }

    public boolean deleteFront() {
        if(isEmpty()) return false;
        h=get(h+1);
        return true;
    }

    public boolean deleteLast() {
        if(isEmpty()) return false;
        t=get(t-1);
        return true;
    }

    public int getFront() {
        if(isEmpty()) return -1;
        return array[h];
    }

    public int getRear() {
        if (isEmpty()) return -1;
        return array[get(t-1)];
    }

    public boolean isEmpty() {
        return h==t;
    }

    public boolean isFull() {
        return get(h-1)==t;
    }
}
```

### [1302. 层数最深叶子节点的和](https://leetcode.cn/problems/deepest-leaves-sum/)

> 给你一棵二叉树的根节点 root ，请你返回 层数最深的叶子节点的和 。
>
>  
>
> 示例 1：
>
> ![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2019/12/28/1483_ex1.png)
>
> 输入：root = [1,2,3,4,5,null,6,7,null,null,null,null,8]
> 输出：15
> 示例 2：
>
> 输入：root = [6,7,8,2,7,1,3,9,null,1,4,null,null,null,5]
> 输出：19
>
>
> 提示：
>
> 树中节点数目在范围 [1, 104] 之间。
> 1 <= Node.val <= 100
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/deepest-leaves-sum
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class Solution {
    public int deepestLeavesSum(TreeNode root) {
        Deque<TreeNode> deque=new LinkedList<>();
        int ans=0;
        deque.offer(root);
        while (!deque.isEmpty()){
            int size=deque.size();
            ans=0;
            for(int i=0;i<size;i++){
                TreeNode temp=deque.poll();
                ans+=temp.val;
                if(temp.left!=null) deque.offer(temp.left);
                if(temp.right!=null) deque.offer(temp.right);
            }
        }
        
        return ans;
    }
}
```

### [1224. 最大相等频率](https://leetcode.cn/problems/maximum-equal-frequency/)

> 给你一个正整数数组 nums，请你帮忙从该数组中找出能满足下面要求的 最长 前缀，并返回该前缀的长度：
>
> 从前缀中 恰好删除一个 元素后，剩下每个数字的出现次数都相同。
> 如果删除这个元素后没有剩余元素存在，仍可认为每个数字都具有相同的出现次数（也就是 0 次）。
>
>  
>
> 示例 1：
>
> 输入：nums = [2,2,1,1,5,3,3,5]
> 输出：7
> 解释：对于长度为 7 的子数组 [2,2,1,1,5,3,3]，如果我们从中删去 nums[4] = 5，就可以得到 [2,2,1,1,3,3]，里面每个数字都出现了两次。
> 示例 2：
>
> 输入：nums = [1,1,1,2,2,2,3,3,3,4,4,4,5]
> 输出：13
>
>
> 提示：
>
> 2 <= nums.length <= 105
> 1 <= nums[i] <= 105
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/maximum-equal-frequency
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class Solution {
    public int maxEqualFreq(int[] nums) {
        //建立查询每个元素的个数、具有相同出现频率的元素个数的hash
        HashMap<Integer, Integer> count = new HashMap<>();
        HashMap<Integer, Integer> fre = new HashMap<>();
        int ans = 0, max_fre = 0;

        for (int i = 0; i < nums.length; i++) {
            //更新某个元素的个数与“频率”的个数
            int num = nums[i];
            int count_num = count.getOrDefault(num, 0);
            if (count_num > 0) {
                fre.put(count_num, fre.get(count_num) - 1);
            }

            //元素个数+1，进行更新
            count_num++;
            count.put(num, count_num);
            //"频率"个数进行更新
            fre.put(count_num, fre.getOrDefault(count_num, 0) + 1);
            max_fre = Math.max(max_fre, count_num);

            /**
             * 如果 1.每个元素都出现一次，随机删除一个就满足要求
             *      2. 去掉一个数num后，其他频率相等【去掉 num 后，num 的个数为0】
             *      3. 去掉一个数num后，其他频率相等【去掉 num 后，num 的个数为和其他元素的个数相同】
             */
            if (max_fre == 1 || max_fre * fre.get(max_fre) == i || max_fre - 1 + (max_fre - 1) * fre.get(max_fre - 1) == i){
                ans=Math.max(ans,i+1);
            }
        }

        return ans;
    }
}
```

###  [1329. 将矩阵按对角线排序](https://leetcode.cn/problems/sort-the-matrix-diagonally/)

> 矩阵对角线 是一条从矩阵最上面行或者最左侧列中的某个元素开始的对角线，沿右下方向一直到矩阵末尾的元素。例如，矩阵 mat 有 6 行 3 列，从 mat[2][0] 开始的 矩阵对角线 将会经过 mat[2][0]、mat[3][1] 和 mat[4][2] 。
>
> 给你一个 m * n 的整数矩阵 mat ，请你将同一条 矩阵对角线 上的元素按升序排序后，返回排好序的矩阵。
>
>  
>
> 示例 1：
>
> ![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2020/01/25/1482_example_1_2.png)
>
> 输入：mat = [[3,3,1,1],[2,2,1,2],[1,1,1,2]]
> 输出：[[1,1,1,1],[1,2,2,2],[1,2,3,3]]
> 示例 2：
>
> 输入：mat = [[11,25,66,1,69,7],[23,55,17,45,15,52],[75,31,36,44,58,8],[22,27,33,25,68,4],[84,28,14,11,5,50]]
> 输出：[[5,17,4,1,52,7],[11,11,25,45,8,69],[14,23,25,44,58,15],[22,27,31,36,50,66],[84,28,75,33,55,68]]
>
>
> 提示：
>
> m == mat.length
> n == mat[i].length
> 1 <= m, n <= 100
> 1 <= mat[i][j] <= 100
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/sort-the-matrix-diagonally
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class Solution {
    public int[][] diagonalSort(int[][] mat) {
        int n = mat.length, m = mat[0].length;//确定行、列数

        for (int b = -(n - 1); b <= m - 1; b++) {//确定截距
            List<Integer> list = new ArrayList<>();//存储对角线上的元素
            for (int x = 0, y = b; x < n && y < m; x++, y++) {
                if (y >= 0)//x和y的上升频率一样，表明是按照k为1上升的，如果y大于0，表明走到了矩阵内
                    list.add(mat[x][y]);
            }
            Collections.sort(list);//排序
            for (int x = 0, y = b, k = 0; x < n && y < m; x++, y++) {
                if (y >= 0)
                    mat[x][y] = list.get(k++);//填充排序后的数字
            }
        }

        return mat;
    }
}
```

1. ![image-20220823094244590](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220823094244590.png)
2. y=x+b.只需要确定截距就可以





# 算法基础课

> 快排模板

```java
    public static void quick_sort(int[] a, int l, int r) {
        if (l >= r) return;

        int x = a[l], i = l - 1, j = r + 1;
        while (i<j){
            do i++; while (a[i]<x);
            do j--;while (a[j]>x);
            if(i<j) {
                int temp=a[i];
                a[i]=a[j];
                a[j]=temp;
            }
        }

        quick_sort(a,l,j);
        quick_sort(a,j+1,r);
    }
```

> 归并排序模板

```java
// 归并排序算法模板（选用）
    public static void mergeSort(int[] q,int l,int r){
        if(l>=r)return;

        int mid = l+r>>1; //向下取整

        //递归处理子问题
        mergeSort(q,l,mid); 
        mergeSort(q,mid+1,r);

        //临时结果数组
        int[] res = new int[r-l+1];

        //两个排好序的数组 合并起来到 临时结果数组
        int i=l,j=mid+1,k=0;//k为暂存数组第几个数
        while(i<=mid&&j<=r){
            if(q[i]<q[j])res[k++]=q[i++];
            else res[k++]=q[j++];
        }

        //剩下的直接拼在结果数组后面
        while(i<=mid)res[k++]=q[i++];
        while(j<=r)res[k++]=q[j++];

        //将临时结果数组 重新赋值给 q
        for(int m=l,n=0;m<=r;m++,n++ )q[m]=res[n];

    }

作者：Xlaoer
链接：https://www.acwing.com/solution/content/91552/
来源：AcWing
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```







> 二分模板

<img src="C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220723131342617.png" alt="image-20220723131342617" style="zoom:50%;" />

二分模板一共有两个，分别适用于不同情况。
算法思路：假设目标值在闭区间[l, r]中， 每次将区间长度缩小一半，当l = r时，我们就找到了目标值。



结论：判断完性质后，如果L=mid：二分时就+1

​											R=mid：二分时不+1



版本1
当我们将区间[l, r]划分成[l, mid]和[mid + 1, r]时，其更新操作是r = mid或者l = mid + 1;，计算mid时不需要加1。

C++ 代码模板：

```java
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        int mid = l + r >> 1;
        if (check(mid)) r = mid;
        else l = mid + 1;
    }
    return l;
}
```

版本2
当我们将区间[l, r]划分成[l, mid - 1]和[mid, r]时，其更新操作是r = mid - 1或者l = mid;，此时为了防止死循环，计算mid时需要加1。

C++ 代码模板：

```c++
int bsearch_2(int l, int r)
{
    while (l < r)
    {
        int mid = l + r + 1 >> 1;
        if (check(mid)) l = mid;
        else r = mid - 1;
    }
    return l;
}
```



> 浮点数二分模板

浮点数二分的本质也是边界, 唯一区别是浮点数没有整除, 区间长度可以严格的缩小一半

当区间长度足够小时, 便可以认为是一个数

模板

```java
double bsearch(double l, double r) {
    const double eps = 1e-6;   // eps 表示精度，取决于题目对精度的要求, 一般比所求精度高 2
    while (r - l > eps) {
        double mid = (l + r) / 2;
        if (check(mid)) r = mid;
        else l = mid;
    }
    return l;
}
```



## 快速排序

### \785. 快速排序

> 给定你一个长度为 nn 的整数数列。
>
> 请你使用快速排序对这个数列按照从小到大进行排序。
>
> 并将排好序的数列按顺序输出。
>
> #### 输入格式
>
> 输入共两行，第一行包含整数 nn。
>
> 第二行包含 nn 个整数（所有整数均在 1∼1091∼109 范围内），表示整个数列。
>
> #### 输出格式
>
> 输出共一行，包含 nn 个整数，表示排好序的数列。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000
>
> #### 输入样例：
>
> ```
> 5
> 3 1 2 4 5
> ```
>
> #### 输出样例：
>
> ```
> 1 2 3 4 5
> ```



```java
package acwing;

import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));//创建一个缓冲流，对节点流进行包装

        int n = Integer.parseInt(br.readLine());
        int[] a = new int[n];
        String[] temp = br.readLine().split(" ");
        for (int i = 0; i < n; i++) a[i] = Integer.parseInt(temp[i]);
        quick_sort(a, 0, n - 1);

        for (int i : a) System.out.print(i + " ");

        br.close();//关闭缓冲流
    }

    public static void quick_sort(int[] a, int l, int r) {
        if (l >= r) return;

        int x = a[l], i = l - 1, j = r + 1;
        while (i<j){
            do i++; while (a[i]<x);
            do j--;while (a[j]>x);
            if(i<j) {
                int temp=a[i];
                a[i]=a[j];
                a[j]=temp;
            }
        }

        quick_sort(a,l,j);
        quick_sort(a,j+1,r);
    }
}
```

###  \786. 第k个数

> 给定一个长度为 nn 的整数数列，以及一个整数 kk，请用快速选择算法求出数列从小到大排序后的第 kk 个数。
>
> #### 输入格式
>
> 第一行包含两个整数 nn 和 kk。
>
> 第二行包含 nn 个整数（所有整数均在 1∼1091∼109 范围内），表示整数数列。
>
> #### 输出格式
>
> 输出一个整数，表示数列的第 kk 小数。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000,
> 1≤k≤n1≤k≤n
>
> #### 输入样例：
>
> ```
> 5 3
> 2 4 1 5 3
> ```
>
> #### 输出样例：
>
> ```
> 3
> ```

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        String[] n_k=br.readLine().split(" ");
        int n=Integer.parseInt(n_k[0]),k=Integer.parseInt(n_k[1]);
        String[] arr=br.readLine().split(" ");
        int[] q=new int[n];
        for(int i=0;i<n;i++) q[i]=Integer.parseInt(arr[i]);

        quick_sort(q,0,n-1);

        System.out.println(q[k-1]);

        br.close();
    }

    public static void quick_sort(int[] q,int l,int r){
        if(l>=r) return;
        int x=q[l],i=l-1,j=r+1;
        while (i<j){
            do i++;while (q[i]<x);
            do j--;while (q[j]>x);
            if(i<j){
                int temp=q[i];
                q[i]=q[j];
                q[j]=temp;
            }
        }

        quick_sort(q,l,j);
        quick_sort(q,j+1,r);
    }
}
```

## 归并排序

### \787. 归并排序

> 给定你一个长度为 nn 的整数数列。
>
> 请你使用归并排序对这个数列按照从小到大进行排序。
>
> 并将排好序的数列按顺序输出。
>
> #### 输入格式
>
> 输入共两行，第一行包含整数 nn。
>
> 第二行包含 nn 个整数（所有整数均在 1∼1091∼109 范围内），表示整个数列。
>
> #### 输出格式
>
> 输出共一行，包含 nn 个整数，表示排好序的数列。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000
>
> #### 输入样例：
>
> ```
> 5
> 3 1 2 4 5
> ```
>
> #### 输出样例：
>
> ```
> 1 2 3 4 5
> ```

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int n = Integer.parseInt(br.readLine());
        String[] arr1 = br.readLine().split(" ");
        int[] arr2 = new int[n];
        for (int i = 0; i < n; i++) arr2[i] = Integer.parseInt(arr1[i]);

        merge_sort(arr2, 0, n - 1);

        for (int i = 0; i < n; i++) System.out.print(arr2[i] + " ");

        br.close();
    }

    public static void  merge_sort(int[] a, int l, int r) {
        if (l >= r) return;

        int mid = r+l >> 1;
        merge_sort(a,l,mid);merge_sort(a,mid+1,r);

        int[] temp=new int[r-l+1];
        int k=0,i=l,j=mid+1;
        while (i<=mid&&j<=r){
            if(a[i]<=a[j]) temp[k++]=a[i++];
            else temp[k++]=a[j++];
        }

        while (i<=mid) temp[k++]=a[i++];
        while (j<=r) temp[k++]=a[j++];

        for(int m=l,n=0;m<=r;m++,n++){
            a[m]=temp[n];
        }
    }
}
```

### \788. 逆序对的数量

> 给定一个长度为 nn 的整数数列，请你计算数列中的逆序对的数量。
>
> 逆序对的定义如下：对于数列的第 ii 个和第 jj 个元素，如果满足 i<ji<j 且 a[i]>a[j]a[i]>a[j]，则其为一个逆序对；否则不是。
>
> #### 输入格式
>
> 第一行包含整数 nn，表示数列的长度。
>
> 第二行包含 nn 个整数，表示整个数列。
>
> #### 输出格式
>
> 输出一个整数，表示逆序对的个数。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000，
> 数列中的元素的取值范围 [1,109][1,109]。
>
> #### 输入样例：
>
> ```
> 6
> 2 3 4 5 6 1
> ```
>
> #### 输出样例：
>
> ```
> 5
> ```

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        int n=Integer.parseInt(br.readLine());
        String[] str=br.readLine().split(" ");
        int[] q=new int[str.length];
        for(int i=0;i<n;i++) q[i]=Integer.parseInt(str[i]);

        System.out.println(merge_sort(q,0,n-1));
        br.close();
    }

    public static long merge_sort(int[] q,int l,int r){
        if(l>=r) return 0;

        int mid=l+r>>1;
        long ans=merge_sort(q,l,mid)+merge_sort(q,mid+1,r);

        int k =0,i=l,j=mid+1;
        int[] temp=new int[r-l+1];
        while (i<=mid&&j<=r){
            if(q[i]<=q[j]) temp[k++]=q[i++];
            else{
                temp[k++]=q[j++];
                ans+=mid-i+1;
            }
        }

        while (i<=mid) temp[k++]=q[i++];
        while (j<=r) temp[k++]=q[j++];

        for(int m=l,n=0;m<=r;m++,n++) q[m]=temp[n];

        return ans;
    }
}
```

## 二分

### \789. 数的范围

> 给定一个按照升序排列的长度为 nn 的整数数组，以及 qq 个查询。
>
> 对于每个查询，返回一个元素 kk 的起始位置和终止位置（位置从 00 开始计数）。
>
> 如果数组中不存在该元素，则返回 `-1 -1`。
>
> #### 输入格式
>
> 第一行包含整数 nn 和 qq，表示数组长度和询问个数。
>
> 第二行包含 nn 个整数（均在 1∼100001∼10000 范围内），表示完整数组。
>
> 接下来 qq 行，每行包含一个整数 kk，表示一个询问元素。
>
> #### 输出格式
>
> 共 qq 行，每行包含两个整数，表示所求元素的起始位置和终止位置。
>
> 如果数组中不存在该元素，则返回 `-1 -1`。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000
> 1≤q≤100001≤q≤10000
> 1≤k≤100001≤k≤10000
>
> #### 输入样例：
>
> ```
> 6 3
> 1 2 2 3 3 4
> 3
> 4
> 5
> ```
>
> #### 输出样例：
>
> ```
> 3 4
> 5 5
> -1 -1
> ```

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        String[] str=br.readLine().split(" ");
        int n=Integer.parseInt(str[0]);
        int count=Integer.parseInt(str[1]);
        int[] q=new int[n];
        str=br.readLine().split(" ");
        for(int i=0;i<n;i++) q[i]=Integer.parseInt(str[i]);

        while (count-->0){
            int x=Integer.parseInt(br.readLine());

            int l=0,r=n-1;
            while (l<r){
                int mid=l+r>>1;
                if(q[mid]>=x){
                    r=mid;
                }else{
                    l=mid+1;
                }
            }
            if(q[l]!=x) System.out.println("-1 -1");
            else{
                System.out.print(l+" ");
                l=0;r=n-1;
                while (l<r){
                    int mid=(l+r+1)>>1;
                    if(q[mid]<=x){
                        l=mid;
                    }else{
                        r=mid-1;
                    }
                }
                System.out.println(l);
            }

        }
    }

}
```

### \790. 数的三次方根

> 给定一个浮点数 nn，求它的三次方根。
>
> #### 输入格式
>
> 共一行，包含一个浮点数 nn。
>
> #### 输出格式
>
> 共一行，包含一个浮点数，表示问题的解。
>
> 注意，结果保留 66 位小数。
>
> #### 数据范围
>
> −10000≤n≤10000−10000≤n≤10000
>
> #### 输入样例：
>
> ```
> 1000.00
> ```
>
> #### 输出样例：
>
> ```
> 10.000000
> ```

```java
import java.io.*;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        double n=Double.parseDouble(br.readLine());

        double l=-100000,r=100000;
        while (r-l>(double)(1e-8)){//1e-8为1^-8
            double mid=(l+r)/2;
            if(mid*mid*mid>=n)r=mid;
            else l=mid;
        }

        System.out.println(String.format("%.6f",l));//输出指定格式
    }
}
```

## 高精度

> BigInteger处理整数
>
> BigDecimal处理小数
>
> 加减乘除：add（）、subtract（）、multiply（）、divide（）
>
> 取余：divideAndRemainder（）【返回值是数组】

## 前缀和

> 模板

```java
int[] q = new int[n+1];
for (int i = 1; i <=n; i++) q[i] = Integer.parseInt(str[i-1]);

int[] pre_sum = new int[n+1];
for (int i = 1; i <= n; i++) pre_sum[i] = q[i] + pre_sum[i - 1];
```

### \795. 前缀和

> 输入一个长度为 nn 的整数序列。
>
> 接下来再输入 mm 个询问，每个询问输入一对 l,rl,r。
>
> 对于每个询问，输出原序列中从第 ll 个数到第 rr 个数的和。
>
> #### 输入格式
>
> 第一行包含两个整数 nn 和 mm。
>
> 第二行包含 nn 个整数，表示整数数列。
>
> 接下来 mm 行，每行包含两个整数 ll 和 rr，表示一个询问的区间范围。
>
> #### 输出格式
>
> 共 mm 行，每行输出一个询问的结果。
>
> #### 数据范围
>
> 1≤l≤r≤n1≤l≤r≤n,
> 1≤n,m≤1000001≤n,m≤100000,
> −1000≤数列中元素的值≤1000−1000≤数列中元素的值≤1000
>
> #### 输入样例：
>
> ```
> 5 3
> 2 1 3 6 4
> 1 2
> 1 3
> 2 4
> ```
>
> #### 输出样例：
>
> ```
> 3
> 6
> 10
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] str = br.readLine().split(" ");
        int n = Integer.parseInt(str[0]), m = Integer.parseInt(str[1]);
        str = br.readLine().split(" ");
        int[] q = new int[n+1];
        for (int i = 1; i <=n; i++) q[i] = Integer.parseInt(str[i-1]);

        int[] pre_sum = new int[n+1];
        for (int i = 1; i <= n; i++) pre_sum[i] = q[i] + pre_sum[i - 1];

        while (m-- > 0) {
            str = br.readLine().split(" ");
            int l = Integer.parseInt(str[0]), r = Integer.parseInt(str[1]);

            System.out.println(pre_sum[r] - pre_sum[l - 1]);
        }

        br.close();
    }
}
```

### 796. 子矩阵的和

> 输入一个 nn 行 mm 列的整数矩阵，再输入 qq 个询问，每个询问包含四个整数 x1,y1,x2,y2x1,y1,x2,y2，表示一个子矩阵的左上角坐标和右下角坐标。
>
> 对于每个询问输出子矩阵中所有数的和。
>
> #### 输入格式
>
> 第一行包含三个整数 n，m，qn，m，q。
>
> 接下来 nn 行，每行包含 mm 个整数，表示整数矩阵。
>
> 接下来 qq 行，每行包含四个整数 x1,y1,x2,y2x1,y1,x2,y2，表示一组询问。
>
> #### 输出格式
>
> 共 qq 行，每行输出一个询问的结果。
>
> #### 数据范围
>
> 1≤n,m≤10001≤n,m≤1000,
> 1≤q≤2000001≤q≤200000,
> 1≤x1≤x2≤n1≤x1≤x2≤n,
> 1≤y1≤y2≤m1≤y1≤y2≤m,
> −1000≤矩阵内元素的值≤1000−1000≤矩阵内元素的值≤1000
>
> #### 输入样例：
>
> ```
> 3 4 3
> 1 7 2 4
> 3 6 2 8
> 2 1 2 3
> 1 1 2 2
> 2 1 3 4
> 1 3 3 4
> ```
>
> #### 输出样例：
>
> ```
> 17
> 27
> 21
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] str=br.readLine().split(" ");
        int n=Integer.parseInt(str[0]),m=Integer.parseInt(str[1]),q=Integer.parseInt(str[2]);
        int[][] arr=new int[n+1][m+1];
        for(int i=1;i<=n;i++){
            String[] temp=br.readLine().split(" ");
            for(int j=1;j<=m;j++){
                arr[i][j]=Integer.parseInt(temp[j-1]);
            }
        }

        int[][] pre_sum=new int[n+1][m+1];
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                pre_sum[i][j]=arr[i][j]+pre_sum[i-1][j]+pre_sum[i][j-1]-pre_sum[i-1][j-1];
            }
        }

        while (q-->0){
            str=br.readLine().split(" ");
            int x1=Integer.parseInt(str[0]),y1=Integer.parseInt(str[1]);
            int x2=Integer.parseInt(str[2]),y2=Integer.parseInt(str[3]);

            System.out.println(pre_sum[x2][y2]-pre_sum[x2][y1-1]-pre_sum[x1-1][y2]+pre_sum[x1-1][y1-1]);
        }

        br.close();
    }
}
```

## 差分

![image-20220724101737751](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920180.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920693.png)

矩阵差分

![image-20220724152054920](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920757.png)



### \797. 差分

> 输入一个长度为 nn 的整数序列。
>
> 接下来输入 mm 个操作，每个操作包含三个整数 l,r,cl,r,c，表示将序列中 [l,r][l,r] 之间的每个数加上 cc。
>
> 请你输出进行完所有操作后的序列。
>
> #### 输入格式
>
> 第一行包含两个整数 nn 和 mm。
>
> 第二行包含 nn 个整数，表示整数序列。
>
> 接下来 mm 行，每行包含三个整数 l，r，cl，r，c，表示一个操作。
>
> #### 输出格式
>
> 共一行，包含 nn 个整数，表示最终序列。
>
> #### 数据范围
>
> 1≤n,m≤1000001≤n,m≤100000,
> 1≤l≤r≤n1≤l≤r≤n,
> −1000≤c≤1000−1000≤c≤1000,
> −1000≤整数序列中元素的值≤1000−1000≤整数序列中元素的值≤1000
>
> #### 输入样例：
>
> ```
> 6 3
> 1 2 2 1 2 1
> 1 3 1
> 3 5 1
> 1 6 1
> ```
>
> #### 输出样例：
>
> ```
> 3 4 5 3 4 2
> ```

```java
package acwing;

import java.io.*;
import java.math.BigInteger;
import java.util.*;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String[] str=br.readLine().split(" ");
        int n=Integer.parseInt(str[0]),m=Integer.parseInt(str[1]);
        str=br.readLine().split(" ");
        int[] q=new int[n+2];
        for(int i=1;i<=n;i++) q[i]=Integer.parseInt(str[i-1]);
        int[] sub_arr=new int[n+2];
        for(int i=1;i<=n;i++) insert(sub_arr,i,i,q[i]);

        while (m-->0){
            str=br.readLine().split(" ");
            int l=Integer.parseInt(str[0]),r=Integer.parseInt(str[1]),num=Integer.parseInt(str[2]);
            insert(sub_arr,l,r,num);
        }

        for(int i=1;i<=n;i++) q[i]=q[i-1]+sub_arr[i];

        for(int i=1;i<=n;i++) System.out.print(q[i]+" ");

        br.close();
    }

    public static void insert(int[] sub_arr,int l,int r,int num){
        sub_arr[l]+=num;
        sub_arr[r+1]-=num;
    }
}
```

优秀版

```java
import java.io.*;

public class Main {
    static BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
    static BufferedWriter log = new BufferedWriter(new OutputStreamWriter(System.out));
    static int N = 100010;  // 数据规模为 10w
    static int[] b = new int[N];    // b数组为 arr数组的差分
    static int[] arr = new int[N];  // arr数组为 b数组的前缀和

    // 对差分数组进行插入操作
    private static void insert(int l, int r, int val) {
        // 可以画图进行理解
        b[l] += val;
        b[r + 1] -= val;
    }

    // 程序入口
    public static void main(String[] args) throws IOException {
        // 初始化输入数据
        String[] s = reader.readLine().split(" ");
        int n = Integer.parseInt(s[0]);
        int m = Integer.parseInt(s[1]);
        String[] sArr = reader.readLine().split(" ");
        for (int i = 1; i <= n; i++)       // 注意下标为 1
            arr[i] = Integer.parseInt(sArr[i - 1]);

        // 初始化 b数组
        for (int i = 1; i <= n; i++) {
            // 相当于将 arr中全部看为 0, 则 b[n]中也全部都为 0, 再在其中区间 [i, i] 添加 arr[i], 求出 b[i]
            insert(i, i, arr[i]);
        }

        // m次循环操作
        while (m-- > 0) {
            String[] sIn = reader.readLine().split(" ");
            int l = Integer.parseInt(sIn[0]), r = Integer.parseInt(sIn[1]), val = Integer.parseInt(sIn[2]);
            insert(l, r, val);
        }

        // 求数组 arr插入元素后的值, 相当于求 b[n]的前缀和
        for (int i = 1; i <= n; i++) {
            arr[i] = arr[i - 1] + b[i];
            log.write(arr[i] + " ");
        }

        // 释放资源
        reader.close();
        log.flush();
        log.close();
    }
}
```

### \798. 差分矩阵

> 输入一个 nn 行 mm 列的整数矩阵，再输入 qq 个操作，每个操作包含五个整数 x1,y1,x2,y2,cx1,y1,x2,y2,c，其中 (x1,y1)(x1,y1) 和 (x2,y2)(x2,y2) 表示一个子矩阵的左上角坐标和右下角坐标。
>
> 每个操作都要将选中的子矩阵中的每个元素的值加上 cc。
>
> 请你将进行完所有操作后的矩阵输出。
>
> #### 输入格式
>
> 第一行包含整数 n,m,qn,m,q。
>
> 接下来 nn 行，每行包含 mm 个整数，表示整数矩阵。
>
> 接下来 qq 行，每行包含 55 个整数 x1,y1,x2,y2,cx1,y1,x2,y2,c，表示一个操作。
>
> #### 输出格式
>
> 共 nn 行，每行 mm 个整数，表示所有操作进行完毕后的最终矩阵。
>
> #### 数据范围
>
> 1≤n,m≤10001≤n,m≤1000,
> 1≤q≤1000001≤q≤100000,
> 1≤x1≤x2≤n1≤x1≤x2≤n,
> 1≤y1≤y2≤m1≤y1≤y2≤m,
> −1000≤c≤1000−1000≤c≤1000,
> −1000≤矩阵内元素的值≤1000−1000≤矩阵内元素的值≤1000
>
> #### 输入样例：
>
> ```
> 3 4 3
> 1 2 2 1
> 3 2 2 1
> 1 1 1 1
> 1 1 2 2 1
> 1 3 2 3 2
> 3 1 3 4 1
> ```
>
> #### 输出样例：
>
> ```
> 2 3 4 1
> 4 3 4 1
> 2 2 2 2
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

public class Main {
    static int n,m,q;
    static int[][] a;
    static int[][] b;
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str=br.readLine().split(" ");
        n=Integer.parseInt(str[0]);m=Integer.parseInt(str[1]);q=Integer.parseInt(str[2]);
        a=new int[n+2][m+2];
        b=new int[n+2][m+2];
        for(int i=1;i<=n;i++){
            str=br.readLine().split(" ");
            for (int j=1;j<=m;j++){
                a[i][j]=Integer.parseInt(str[j-1]);
            }
        }

        for (int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                insert(i,j,i,j,a[i][j]);
            }
        }

        while (q-->0){
            str=br.readLine().split(" ");
            int x1=Integer.parseInt(str[0]),y1=Integer.parseInt(str[1]),x2=Integer.parseInt(str[2]),y2=Integer.parseInt(str[3]),num=Integer.parseInt(str[4]);
            insert(x1,y1,x2,y2,num);
        }

        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                b[i][j]+=b[i-1][j]+b[i][j-1]-b[i-1][j-1];
            }
        }

        for(int i=1;i<=n;i++){
            for (int j=1;j<=m;j++){
                bw.write(b[i][j]+" ");
            }
            bw.newLine();
        }

        bw.flush();
        bw.close();
        br.close();
    }
    public static void insert(int x1,int y1,int x2,int y2,int num){
        b[x1][y1]+=num;
        b[x2+1][y1]-=num;
        b[x1][y2+1]-=num;
        b[x2+1][y2+1]+=num;
    }
}
```

1. bw.write(b[i][j]+" ");记得添加“ ”，否则会乱码

## 双指针

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920029.png)

 ### \799. 最长连续不重复子序列

> 给定一个长度为 nn 的整数序列，请找出最长的不包含重复的数的连续区间，输出它的长度。
>
> #### 输入格式
>
> 第一行包含整数 nn。
>
> 第二行包含 nn 个整数（均在 0∼1050∼105 范围内），表示整数序列。
>
> #### 输出格式
>
> 共一行，包含一个整数，表示最长的不包含重复的数的连续区间的长度。
>
> #### 数据范围
>
> 1≤n≤1051≤n≤105
>
> #### 输入样例：
>
> ```
> 5
> 1 2 2 3 5
> ```
>
> #### 输出样例：
>
> ```
> 3
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

public class Main {
    static int N=100010;
    static int n,m,q;
    static int[] a=new int[N];
    static int[] b=new int[N];
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));
        n=Integer.parseInt(br.readLine());
        String[] str=br.readLine().split(" ");
        for(int i=0;i<n;i++) a[i]=Integer.parseInt(str[i]);
        int ans=0;

        for(int i=0,j=0;i<n;i++){
            b[a[i]]++;
            while (b[a[i]]>1){
                b[a[j]]--;
                j++;
            }
            ans=Math.max(ans,i-j+1);
        }

        bw.write(ans+"");

        bw.flush();
        bw.close();
        br.close();
    }
}
```

![image-20220724215446200](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920451.png)

### \800. 数组元素的目标和

> 给定两个升序排序的有序数组 AA 和 BB，以及一个目标值 xx。
>
> 数组下标从 00 开始。
>
> 请你求出满足 A[i]+B[j]=xA[i]+B[j]=x 的数对 (i,j)(i,j)。
>
> 数据保证有唯一解。
>
> #### 输入格式
>
> 第一行包含三个整数 n,m,xn,m,x，分别表示 AA 的长度，BB 的长度以及目标值 xx。
>
> 第二行包含 nn 个整数，表示数组 AA。
>
> 第三行包含 mm 个整数，表示数组 BB。
>
> #### 输出格式
>
> 共一行，包含两个整数 ii 和 jj。
>
> #### 数据范围
>
> 数组长度不超过 105105。
> 同一数组内元素各不相同。
> 1≤数组元素≤1091≤数组元素≤109
>
> #### 输入样例：
>
> ```
> 4 5 6
> 1 2 4 7
> 3 4 6 8 9
> ```
>
> #### 输出样例：
>
> ```
> 1 1
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

public class Main {
    static int N=100010;
    static int n,m,q;
    static int[] a=new int[N];
    static int[] b=new int[N];
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str=br.readLine().split(" ");
        n=Integer.parseInt(str[0]);
        m=Integer.parseInt(str[1]);
        q=Integer.parseInt(str[2]);
        str=br.readLine().split(" ");
        for(int i=0;i<n;i++){
            a[i]=Integer.parseInt(str[i]);
        }
        str=br.readLine().split(" ");
        for(int i=0;i<m;i++){
            b[i]=Integer.parseInt(str[i]);
        }
        for(int i=0,j=m-1;i<n;i++){
            while (j>=0&&a[i]+b[j]>q) j--;
            if(a[i]+b[j]==q){
                bw.write(i+" "+j);
                break;
            }
        }

        bw.flush();
        bw.close();
        br.close();
    }
}
```

### \2816. 判断子序列

> 给定一个长度为 nn 的整数序列 a1,a2,…,ana1,a2,…,an 以及一个长度为 mm 的整数序列 b1,b2,…,bmb1,b2,…,bm。
>
> 请你判断 aa 序列是否为 bb 序列的子序列。
>
> 子序列指序列的一部分项按**原有次序排列**而得的序列，例如序列 {a1,a3,a5}{a1,a3,a5} 是序列 {a1,a2,a3,a4,a5}{a1,a2,a3,a4,a5} 的一个子序列。
>
> #### 输入格式
>
> 第一行包含两个整数 n,mn,m。
>
> 第二行包含 nn 个整数，表示 a1,a2,…,ana1,a2,…,an。
>
> 第三行包含 mm 个整数，表示 b1,b2,…,bmb1,b2,…,bm。
>
> #### 输出格式
>
> 如果 aa 序列是 bb 序列的子序列，输出一行 `Yes`。
>
> 否则，输出 `No`。
>
> #### 数据范围
>
> 1≤n≤m≤1051≤n≤m≤105,
> −109≤ai,bi≤109−109≤ai,bi≤109
>
> #### 输入样例：
>
> ```
> 3 5
> 1 3 5
> 1 2 3 4 5
> ```
>
> #### 输出样例：
>
> ```
> Yes
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N=100010;
    static int n,m,q;
    static int[] a=new int[N];
    static int[] b=new int[N];
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str=br.readLine().split(" ");
        n=Integer.parseInt(str[0]);
        m=Integer.parseInt(str[1]);

        str=br.readLine().split(" ");
        for(int i=0;i<n;i++){
            a[i]=Integer.parseInt(str[i]);
        }
        str=br.readLine().split(" ");
        for(int i=0;i<m;i++){
            b[i]=Integer.parseInt(str[i]);
        }

        int i=0,j=0;
        while (i<n&&j<m){
            if(a[i]==b[j]){
                i++;
                j++;
            }
            else j++;
            if(i==n){
                System.out.println("Yes");
                return;
            }
        }

        System.out.println("No");

        bw.flush();
        bw.close();
        br.close();
    }

}
```

## 位运算

![image-20220809204408973](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920970.png)

![](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220809205257613.png)

![image-20220809205545364](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220809205545364.png)

[地址](https://www.acwing.com/solution/AcWing/content/4707/)
![image-20220809210156420](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220809210156420.png)

### \801. 二进制中1的个数

> 给定一个长度为 nn 的数列，请你求出数列中每个数的二进制表示中 11 的个数。
>
> #### 输入格式
>
> 第一行包含整数 nn。
>
> 第二行包含 nn 个整数，表示整个数列。
>
> #### 输出格式
>
> 共一行，包含 nn 个整数，其中的第 ii 个数表示数列中的第 ii 个数的二进制表示中 11 的个数。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000,
> 0≤数列中元素的值≤1090≤数列中元素的值≤109
>
> #### 输入样例：
>
> ```
> 5
> 1 2 3 4 5
> ```
>
> #### 输出样例：
>
> ```
> 1 1 2 1 2
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N=100010;
    static int n,m,q;
    static int[] a=new int[N];
    static int[] b=new int[N];
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));
        n=Integer.parseInt(br.readLine());
        String[] str=br.readLine().split(" ");
        a=new int[n];
        for(int i=0;i<n;i++) a[i]=Integer.parseInt(str[i]);

        for(int i:a){
            int ans=0;
            while (i!=0){
                i-=low_bit(i);
                ans++;
            }
            bw.write(ans+" ");
        }

        bw.flush();
        bw.close();
        br.close();
    }

    public static int low_bit(int i){
        return i&-i;
    }

}
```

## 离散化

![image-20220810141448543](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920475.png)

![image-20220810141910037](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220810141910037.png)

![image-20220810141547372](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220810141547372.png)

### \802. 区间和

> 假定有一个无限长的数轴，数轴上每个坐标上的数都是 00。
>
> 现在，我们首先进行 nn 次操作，每次操作将某一位置 xx 上的数加 cc。
>
> 接下来，进行 mm 次询问，每个询问包含两个整数 ll 和 rr，你需要求出在区间 [l,r][l,r] 之间的所有数的和。
>
> #### 输入格式
>
> 第一行包含两个整数 nn 和 mm。
>
> 接下来 nn 行，每行包含两个整数 xx 和 cc。
>
> 再接下来 mm 行，每行包含两个整数 ll 和 rr。
>
> #### 输出格式
>
> 共 mm 行，每行输出一个询问中所求的区间内数字和。
>
> #### 数据范围
>
> −109≤x≤109−109≤x≤109,
> 1≤n,m≤1051≤n,m≤105,
> −109≤l≤r≤109−109≤l≤r≤109,
> −10000≤c≤10000−10000≤c≤10000
>
> #### 输入样例：
>
> ```
> 3 3
> 1 2
> 3 6
> 7 5
> 1 3
> 4 6
> 7 8
> ```
>
> #### 输出样例：
>
> ```
> 8
> 0
> 5
> ```

````java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N=100010;
    static int n,m,q;
    static int[] a;
    static int[] b;
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));

        String[] str=br.readLine().split(" ");
        n=Integer.parseInt(str[0]);m=Integer.parseInt(str[1]);
        int[][] q=new int[m][2];
        TreeMap<Integer,Integer> treeMap=new TreeMap<>();

        //离散化赋值
        for(int i=0;i<n;i++){
            str=br.readLine().split(" ");
            int a=Integer.parseInt(str[0]),b=Integer.parseInt(str[1]);
            treeMap.put(a,treeMap.getOrDefault(a,0)+b);
        }

        //边界赋值
        for(int i=0;i<m;i++){
            str=br.readLine().split(" ");
            q[i][0]=Integer.parseInt(str[0]);q[i][1]=Integer.parseInt(str[1]);

            treeMap.put(q[i][0],treeMap.getOrDefault(q[i][0],0));
            treeMap.put(q[i][1],treeMap.getOrDefault(q[i][1],0));
        }

        //前缀和
        Object[] key=treeMap.keySet().toArray();
        for(int i=1;i< key.length;i++){
            treeMap.put((Integer) key[i],treeMap.get(key[i-1])+treeMap.get(key[i]));
        }

        //求区间
        for(int i=0;i<m;i++){
            int l=q[i][0],r=q[i][1];

            treeMap.put(l,treeMap.getOrDefault(l,0));
            treeMap.put(r,treeMap.getOrDefault(r,0));
            if(l==(Integer)key[0] ){
                bw.write(treeMap.ceilingEntry(r).getValue()+"");
                bw.newLine();
            }else {
                bw.write(treeMap.ceilingEntry(r).getValue()-treeMap.floorEntry(l-1).getValue()+"");
                bw.newLine();
            }
        }

        bw.flush();
        bw.close();
        br.close();
    }

}
````

## 区间合并

![image-20220810202600706](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920454.png)

### \803. 区间合并

> 给定 nn 个区间 [li,ri][li,ri]，要求合并所有有交集的区间。
>
> 注意如果在端点处相交，也算有交集。
>
> 输出合并完成后的区间个数。
>
> 例如：[1,3][1,3] 和 [2,6][2,6] 可以合并为一个区间 [1,6][1,6]。
>
> #### 输入格式
>
> 第一行包含整数 nn。
>
> 接下来 nn 行，每行包含两个整数 ll 和 rr。
>
> #### 输出格式
>
> 共一行，包含一个整数，表示合并区间完成后的区间个数。
>
> #### 数据范围
>
> 1≤n≤1000001≤n≤100000,
> −109≤li≤ri≤109−109≤li≤ri≤109
>
> #### 输入样例：
>
> ```
> 5
> 1 2
> 2 4
> 5 6
> 7 8
> 7 9
> ```
>
> #### 输出样例：
>
> ```
> 3
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N=100010;
    static int n,m,q;
    static int[] a;
    static int[] b;
    public static void main(String[] args) throws Exception {
        BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw=new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        n=Integer.parseInt(br.readLine());
        List<int[]> list=new ArrayList<>();
        for(int i=0;i<n;i++){
            str=br.readLine().split(" ");
            int l=Integer.parseInt(str[0]),r=Integer.parseInt(str[1]);
            list.add(new int[]{l,r});
        }

        Collections.sort(list,((o1, o2) -> o1[0]-o2[0]));

        int ans=0;
        int r=Integer.MIN_VALUE;
        for(int[] i:list){
            if(i[0]>r){
                ans++;
            }
            r=Math.max(r,i[1]);
        }

        bw.write(ans+"");

        bw.flush();
        bw.close();
        br.close();
    }

}
```

## 栈

### \3302. 表达式求值

> 给定一个表达式，其中运算符仅包含 `+,-,*,/`（加 减 乘 整除），可能包含括号，请你求出表达式的最终值。
>
> **注意：**
>
> - 数据保证给定的表达式合法。
> - 题目保证符号 `-` 只作为减号出现，不会作为负号出现，例如，`-1+2`,`(2+2)*(-(1+1)+2)` 之类表达式均不会出现。
> - 题目保证表达式中所有数字均为正整数。
> - 题目保证表达式在中间计算过程以及结果中，均不超过 231−1231−1。
> - 题目中的整除是指向 00 取整，也就是说对于大于 00 的结果向下取整，例如 5/3=15/3=1，对于小于 00 的结果向上取整，例如 5/(1−4)=−15/(1−4)=−1。
> - C++和Java中的整除默认是向零取整；Python中的整除`//`默认向下取整，因此Python的`eval()`函数中的整除也是向下取整，在本题中不能直接使用。
>
> #### 输入格式
>
> 共一行，为给定表达式。
>
> #### 输出格式
>
> 共一行，为表达式的结果。
>
> #### 数据范围
>
> 表达式的长度不超过 105105。
>
> #### 输入样例：
>
> ```
> (2+2)*(1+1)
> ```
>
> #### 输出样例：
>
> ```
> 8
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N = 100010;
    static int n, m, q;
    static int[] a;
    static int[] b;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        String s1 = br.readLine();//字符串
        n = s1.length();//长度
        Deque<Integer> num = new ArrayDeque<>();//存储数字
        Deque<Character> characters = new ArrayDeque<>();//存储运算符
        HashMap<Character, Integer> hashMap = new HashMap<>();//存储优先级
        hashMap.put('+', 1);
        hashMap.put('-', 1);
        hashMap.put('*', 2);
        hashMap.put('/', 2);

        for (int i = 0; i < n;i++) {
            char c = s1.charAt(i);//当前字符
            if (Character.isDigit(c)) {//如果是数字
                int x = 0;
                while (i < n && Character.isDigit(s1.charAt(i))) {
                    x = x * 10 + s1.charAt(i) - '0';
                    i++;
                }
                num.push(x);//加入栈中
                i--;
            } else if (c == '(') {//如果是括号，加入符号栈
                characters.push(c);
            } else if (c == ')') {//如果是反括号，就进行计算
                while (characters.peek() != '(') {
                    calculate(num, characters);
                }

                characters.poll();//去除左括号
            } else {//如果是运算符
                while (!characters.isEmpty() && characters.peek() != '(' && hashMap.get(characters.peek()) >= hashMap.get(c)) {
                    calculate(num, characters);
                }
                characters.push(c);
            }
        }

        while (!characters.isEmpty()){
            calculate(num,characters);
        }
        
        bw.write(num.poll() + "");

        bw.flush();
        bw.close();
        br.close();
    }

    public static void calculate(Deque<Integer> num, Deque<Character> characters) {
        int b = num.poll();
        int a = num.poll();
        char c = characters.poll();

        if (c == '+') {
            num.push(a + b);
        } else if (c == '-') {
            num.push(a - b);
        } else if (c == '*') {
            num.push(a * b);
        } else {
            num.push(a / b);
        }
    }
}
```

1. 数字栈+符号栈+是否运算优先级
2. ![image-20220811134134435](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220811134134435.png)
3. [地址](https://www.acwing.com/solution/content/40978/)

## 单调栈

![image-20220811195812060](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920590.png)

### \830. 单调栈

> 给定一个长度为 NN 的整数数列，输出每个数左边第一个比它小的数，如果不存在则输出 −1−1。
>
> #### 输入格式
>
> 第一行包含整数 NN，表示数列长度。
>
> 第二行包含 NN 个整数，表示整数数列。
>
> #### 输出格式
>
> 共一行，包含 NN 个整数，其中第 ii 个数表示第 ii 个数的左边第一个比它小的数，如果不存在则输出 −1−1。
>
> #### 数据范围
>
> 1≤N≤1051≤N≤105
> 1≤数列中元素≤1091≤数列中元素≤109
>
> #### 输入样例：
>
> ```
> 5
> 3 4 2 7 5
> ```
>
> #### 输出样例：
>
> ```
> -1 3 -1 2 2
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N = 100010;
    static int n, m, q;
    static int[] a;
    static int[] b;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        n=Integer.parseInt(br.readLine());
        a=new int[n];
        str=br.readLine().split(" ");
        for(int i=0;i<n;i++) a[i]=Integer.parseInt(str[i]);

        Deque<Integer> deque=new ArrayDeque<>();
        for(int i=0;i<n;i++){
            while (!deque.isEmpty()&&deque.peek()>=a[i]){
                deque.poll();
            }
            if(deque.isEmpty()) bw.write(-1+" ");
            else bw.write(deque.peek()+" ");
            deque.push(a[i]);
        }

        bw.flush();
        bw.close();
        br.close();
    }

}
```

## 单调队列

![image-20220811202200480](https://cdn.jsdelivr.net/gh/yzk656/image/202212241920148.png)

![image-20220811202346566](C:/Users/Demon%20Night/AppData/Roaming/Typora/typora-user-images/image-20220811202346566.png)

![image-20220813172324889](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921989.png)

![image-20220813173632199](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921210.png)

### \154. 滑动窗口

> 给定一个大小为 n≤106n≤106 的数组。
>
> 有一个大小为 kk 的滑动窗口，它从数组的最左边移动到最右边。
>
> 你只能在窗口中看到 kk 个数字。
>
> 每次滑动窗口向右移动一个位置。
>
> 以下是一个例子：
>
> 该数组为 `[1 3 -1 -3 5 3 6 7]`，kk 为 33。
>
> | 窗口位置            | 最小值 | 最大值 |
> | :------------------ | :----- | :----- |
> | [1 3 -1] -3 5 3 6 7 | -1     | 3      |
> | 1 [3 -1 -3] 5 3 6 7 | -3     | 3      |
> | 1 3 [-1 -3 5] 3 6 7 | -3     | 5      |
> | 1 3 -1 [-3 5 3] 6 7 | -3     | 5      |
> | 1 3 -1 -3 [5 3 6] 7 | 3      | 6      |
> | 1 3 -1 -3 5 [3 6 7] | 3      | 7      |
>
> 你的任务是确定滑动窗口位于每个位置时，窗口中的最大值和最小值。
>
> #### 输入格式
>
> 输入包含两行。
>
> 第一行包含两个整数 nn 和 kk，分别代表数组长度和滑动窗口的长度。
>
> 第二行有 nn 个整数，代表数组的具体数值。
>
> 同行数据之间用空格隔开。
>
> #### 输出格式
>
> 输出包含两个。
>
> 第一行输出，从左至右，每个位置滑动窗口中的最小值。
>
> 第二行输出，从左至右，每个位置滑动窗口中的最大值。
>
> #### 输入样例：
>
> ```
> 8 3
> 1 3 -1 -3 5 3 6 7
> ```
>
> #### 输出样例：
>
> ```
> -1 -3 -3 -3 3 3
> 3 3 5 5 6 7
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N = 100010;
    static int n, m, q;
    static int[] a;
    static int[] b;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        str = br.readLine().split(" ");
        n = Integer.parseInt(str[0]);
        m = Integer.parseInt(str[1]);
        a = new int[n];
        str = br.readLine().split(" ");
        for (int i = 0; i < n; i++) a[i] = Integer.parseInt(str[i]);

        Deque<Integer> deque = new ArrayDeque<>();
        for (int i = 0; i < m; i++) {
            while (!deque.isEmpty() && a[deque.peekLast()] >= a[i])
                deque.pollLast();
            deque.offerLast(i);
        }
        bw.write(a[deque.peek()] + " ");

        for (int i = m; i < n; i++) {
            while (!deque.isEmpty() && a[deque.peekLast()] >= a[i]) {
                deque.pollLast();
            }
            deque.offerLast(i);
            while (deque.peekFirst() <= i - m) {
                deque.pollFirst();
            }
            bw.write(a[deque.peekFirst()] + " ");
        }

        deque.clear();

        bw.newLine();

        for (int i = 0; i < m; i++) {
            while (!deque.isEmpty() && a[deque.peekLast()] <= a[i]) {
                deque.pollLast();
            }
            deque.offerLast(i);
        }
        bw.write(a[deque.peekFirst()] + " ");
        for (int i = m; i < n; i++) {
            while (!deque.isEmpty() && a[deque.peekLast()] <= a[i]) {
                deque.pollLast();
            }
            deque.offerLast(i);
            while (deque.peekFirst() <= i - m) {
                deque.pollFirst();
            }
            bw.write(a[deque.peekFirst()] + " ");
        }

        bw.flush();
        bw.close();
        br.close();
    }

}
```

##  Tire

![image-20220822172020555](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921878.png)

![image-20220822172011706](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921133.png)

## 并查集

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921599.png)

![](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921107.png)

> 并查集模板

```java
public static int[] p;

//初始化
for(int i=0;i<n;++i) p[i]=i;

//返回x的祖宗节点+路径压缩
public static int find(int x){
    if(p[x]!=x) p[x]=find(p[x]);
    //一定要返回祖宗节点，如果返回x，返回的就是传入的参数值
    return p[x];
}


p[find(a)] = find(b);
```

### \836. 合并集合

> 一共有 nn 个数，编号是 1∼n1∼n，最开始每个数各自在一个集合中。
>
> 现在要进行 mm 个操作，操作共有两种：
>
> 1. `M a b`，将编号为 aa 和 bb 的两个数所在的集合合并，如果两个数已经在同一个集合中，则忽略这个操作；
> 2. `Q a b`，询问编号为 aa 和 bb 的两个数是否在同一个集合中；
>
> #### 输入格式
>
> 第一行输入整数 nn 和 mm。
>
> 接下来 mm 行，每行包含一个操作指令，指令为 `M a b` 或 `Q a b` 中的一种。
>
> #### 输出格式
>
> 对于每个询问指令 `Q a b`，都要输出一个结果，如果 aa 和 bb 在同一集合内，则输出 `Yes`，否则输出 `No`。
>
> 每个结果占一行。
>
> #### 数据范围
>
> 1≤n,m≤1051≤n,m≤105
>
> #### 输入样例：
>
> ```
> 4 5
> M 1 2
> M 3 4
> Q 1 2
> Q 1 3
> Q 3 4
> ```
>
> #### 输出样例：
>
> ```
> Yes
> No
> Yes
> ```

```java
package acwing;

import org.junit.Test;

import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N = 100010;
    static int[] p=new int[N];
    static int n,m;
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        str=br.readLine().split(" ");
        n=Integer.parseInt(str[0]);m=Integer.parseInt(str[1]);
        
        //初始化
        for(int i=0;i<n;++i) p[i]=i;

        while (m--!=0){
            str=br.readLine().split(" ");
            int a=Integer.parseInt(str[1]),b=Integer.parseInt(str[2]);
            if(str[0].equals("M")){
                //a连接到b集合里面
                p[find(a)]=find(b);
            }else{
                if(find(a)==find(b)) {
                    bw.write("Yes");
                    bw.newLine();
                } else {
                    bw.write("No");
                    bw.newLine();
                }
            }
        }


        bw.flush();
        bw.close();
        br.close();
    }

    //返回x的祖宗节点+路径压缩
    public static int find(int x){
        if(p[x]!=x) p[x]=find(p[x]);
        //一定要返回祖宗节点，如果返回x，返回的就是传入的参数值
        return p[x];
    }

}
```

### \837. 连通块中点的数量

> 给定一个包含 nn 个点（编号为 1∼n1∼n）的无向图，初始时图中没有边。
>
> 现在要进行 mm 个操作，操作共有三种：
>
> 1. `C a b`，在点 aa 和点 bb 之间连一条边，aa 和 bb 可能相等；
> 2. `Q1 a b`，询问点 aa 和点 bb 是否在同一个连通块中，aa 和 bb 可能相等；
> 3. `Q2 a`，询问点 aa 所在连通块中点的数量；
>
> #### 输入格式
>
> 第一行输入整数 nn 和 mm。
>
> 接下来 mm 行，每行包含一个操作指令，指令为 `C a b`，`Q1 a b` 或 `Q2 a` 中的一种。
>
> #### 输出格式
>
> 对于每个询问指令 `Q1 a b`，如果 aa 和 bb 在同一个连通块中，则输出 `Yes`，否则输出 `No`。
>
> 对于每个询问指令 `Q2 a`，输出一个整数表示点 aa 所在连通块中点的数量
>
> 每个结果占一行。
>
> #### 数据范围
>
> 1≤n,m≤1051≤n,m≤105
>
> #### 输入样例：
>
> ```
> 5 5
> C 1 2
> Q1 1 2
> Q2 1
> C 2 5
> Q2 5
> ```
>
> #### 输出样例：
>
> ```
> Yes
> 2
> 3
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;

class Main {
    static int N = 100010;
    static int[] p = new int[N];
    static int[] size = new int[N];
    static int n, m;

    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        String[] str;

        str = br.readLine().split(" ");
        n = Integer.parseInt(str[0]);
        m = Integer.parseInt(str[1]);

        //初始化
        for (int i = 0; i < n; ++i) {
            p[i] = i;
            size[i] = 1;
        }

        while (m-- != 0) {
            str = br.readLine().split(" ");
            int a = Integer.parseInt(str[1]);

            if (str[0].equals("C")) {
                int b = Integer.parseInt(str[2]);
                //a连接到b集合里面
                if (find(a) == find(b)) continue;
                size[find(b)] += size[find(a)];
                p[find(a)] = find(b);
            } else if (str[0].equals("Q1")) {
                int b = Integer.parseInt(str[2]);
                if (find(a) == find(b)) {
                    bw.write("Yes");
                    bw.newLine();
                } else {
                    bw.write("No");
                    bw.newLine();
                }
            } else {
                bw.write(size[find(a)]+"");
                bw.newLine();
            }
        }

        bw.flush();
        bw.close();
        br.close();
    }

    //返回x的祖宗节点+路径压缩
    public static int find(int x) {
        if (p[x] != x) p[x] = find(p[x]);
        //一定要返回祖宗节点，如果返回x，返回的就是传入的参数值
        return p[x];
    }

}

```

## 时钟

#### [1344. 时钟指针的夹角](https://leetcode.cn/problems/angle-between-hands-of-a-clock/

> 给你两个数 hour 和 minutes 。请你返回在时钟上，由给定时间的时针和分针组成的较小角的角度（60 单位制）。
>
>  
>
> 示例 1：
>
> <img src="https://cdn.jsdelivr.net/gh/yzk656/image/202212241921871.png" alt="img" style="zoom:25%;" />
>
> 输入：hour = 12, minutes = 30
> 输出：165
> 示例 2：
>
> <img src="https://cdn.jsdelivr.net/gh/yzk656/image/202212241921058.png" alt="img" style="zoom:25%;" />
>
> 输入：hour = 3, minutes = 30
> 输出；75
> 示例 3：
>
> <img src="https://cdn.jsdelivr.net/gh/yzk656/image/202212241921168.png" alt="img" style="zoom:25%;" />
>
> 输入：hour = 3, minutes = 15
> 输出：7.5
> 示例 4：
>
> 输入：hour = 4, minutes = 50
> 输出：155
> 示例 5：
>
> 输入：hour = 12, minutes = 0
> 输出：0
>
>
> 提示：
>
> 1 <= hour <= 12
> 0 <= minutes <= 59
> 与标准答案误差在 10^-5 以内的结果都被视为正确结果。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode.cn/problems/angle-between-hands-of-a-clock
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

```java
class Solution {
    public double angleClock(int hour, int minutes) {
        hour%=12;
        double x=hour*30+minutes*0.5;
        double y=minutes*6;
        return Math.min(Math.abs(x-y),360-Math.abs(x-y));
    }
}
```

## Dijkstra

### \849. Dijkstra求最短路 I

> 给定一个 nn 个点 mm 条边的有向图，图中可能存在重边和自环，所有边权均为正值。
>
> 请你求出 11 号点到 nn 号点的最短距离，如果无法从 11 号点走到 nn 号点，则输出 −1−1。
>
> #### 输入格式
>
> 第一行包含整数 nn 和 mm。
>
> 接下来 mm 行每行包含三个整数 x,y,zx,y,z，表示存在一条从点 xx 到点 yy 的有向边，边长为 zz。
>
> #### 输出格式
>
> 输出一个整数，表示 11 号点到 nn 号点的最短距离。
>
> 如果路径不存在，则输出 −1−1。
>
> #### 数据范围
>
> 1≤n≤5001≤n≤500,
> 1≤m≤1051≤m≤105,
> 图中涉及边长均不超过10000。
>
> #### 输入样例：
>
> ```
> 3 3
> 1 2 2
> 2 3 1
> 1 3 4
> ```
>
> #### 输出样例：
>
> ```
> 3
> ```

```java
import java.io.*;
import java.math.BigInteger;
import java.util.*;
import java.util.function.IntFunction;
import java.util.stream.Collectors;

class Node {
    int x, y, z;

    public Node(int x, int y, int z) {
        this.x = x;
        this.y = y;
        this.z = z;
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), m = sc.nextInt();
        HashMap<Integer, List<int[]>> hashMap = new HashMap<>();
        for (int i = 0; i < m; i++) {
            int x = sc.nextInt(), y = sc.nextInt(), z = sc.nextInt();
            hashMap.computeIfAbsent(x, key -> new ArrayList<>()).add(new int[]{y, z});
        }

        PriorityQueue<int[]> pq = new PriorityQueue<>((o1, o2) -> o1[1] - o2[1]);
        pq.offer(new int[]{1, 0});
        Set<Integer> visit = new HashSet<>();
        visit.add(1);
        int[] dist = new int[n + 1];
        Arrays.fill(dist, 0x3f3f3f);
        dist[1] = 0;

        while (!pq.isEmpty()) {
            int[] cur = pq.poll();
            int cur_node = cur[0], cur_dist = cur[1];
            for (int[] i : hashMap.getOrDefault(cur_node, new ArrayList<>())) {
                int next_node = i[0], next_dist = i[1];
                if (!visit.contains(next_node) || dist[cur_node] + next_dist < dist[next_node]) {
                    dist[next_node] = dist[cur_node] + next_dist;
                    pq.offer(new int[]{next_node, next_dist});
                    visit.add(next_node);
                }
            }
        }
        if (dist[n] == 0x3f3f3f) {
            System.out.println(-1);
        } else System.out.println(dist[n]);
    }
}
```

## 二分图

```java

```



## 匈牙利算法

![image-20220902230858150](https://cdn.jsdelivr.net/gh/yzk656/image/202212241921576.png)

​	
