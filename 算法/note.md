# 01、算法分析  
研究算法的最终目的就是如何花更少的时间，如何占用更少的内存去完成相同的需求。有关算法时间耗费分析，我们称之为算法的时间复杂度分析，有关算法的空间耗费分析，我们称之为算法的空间复杂度分析。  
## 1.1算法的时间复杂度分析  
### 1.1.1事后分析估算方法  
这种统计方法主要是通过设计好的测试程序和测试数据，利用计算机计时器对不同的算法编制的程序的运行时间进行比较，从而确定算法效率的高低，但是这种方法有很大的缺陷：必须依据算法实现编制好的测试程序，通常要花费大量时间和精力，测试完了如果发现测试的是非常糟糕的算法，那么之前所做的事情就全部白费了，并且不同的测试环境(硬件环境)的差别导致测试的结果差异也很大。
### 1.1.2事前分析估算方法  
在计算机程序编写前，依据统计方法对算法进行估算，经过总结，我们发现一个高级语言编写的程序程序在计算机上运行所消耗的时间取决于下列因素：  
 1.算法采用的策略和方案；  
 2.编译产生的代码质量；  
 3.问题的输入规模(所谓的问题输入规模就是输入量的多少)；  
 4.机器执行指令的速度；  
由此可见，抛开这些与计算机硬件、软件有关的因素，一个程序的运行时间依赖于算法的好坏和问题的输入规模。如果算法固定，那么该算法的执行时间就只和问题的输入规模有关系了。  
# 02、排序算法  
在程序中，排序是非常常见的一种需求，提供一些数据元素，把这些数据元素按照一定的规则进行排序。比如查询一些订单，按照订单的日期进行排序；再比如查询一些商品，按照商品的价格进行排序等等。  
## 2.1冒泡排序  
冒泡排序（Bubble Sort），是一种计算机科学领域的较简单的排序算法。以其“在排序过程中相邻元素不断交换，一些元素慢慢被换到最后，看起来就像是元素在冒泡一样”而得名，是一种简单的基于关键词比较的排序算法。  
### 2.1.1排序原理  
1. 比较相邻的元素。如果前一个元素比后一个元素大，就需要一个“中介值”来存储大的那个元素,然后通过“中介值”交换这两个元素的位置。
2. 对每一对相邻元素做同样的工作，从开始第一对元素到结尾的最后一对元素。最终最后位置的元素就是最大值。  
**例子**  
排序前：{4，5，6，3，2，1}  
排序后：{1，2，3，4，5，6}

	<table>
    	<tr>
        	<th>冒泡次数</th>
        	<th colspan="6" align="center">冒泡结果</th>
    	</tr>
    	<tr>
        	<td>初始状态</td>
        	<td>4</td>
			<td>5</td>
			<td>6</td>
			<td>3</td>
			<td>2</td>
			<td>1</td>
    	</tr>
    	<tr>
        	<td>第1次冒泡</td>
        	<td>4</td>
			<td>5</td>
			<td>3</td>
			<td>2</td>
			<td>1</td>
			<td bgcolor="red">6</td>
    	</tr>
		<tr>
    		<td>第2次冒泡</td>
        	<td>4</td>
			<td>3</td>
			<td>2</td>
			<td>1</td>
			<td bgcolor="red">5</td>
			<td bgcolor="green">6</td>
    	</tr>
		<tr>
        	<td>第3次冒泡</td>
        	<td>3</td>
			<td>2</td>
			<td>1</td>
			<td bgcolor="red">4</td>
			<td bgcolor="green">5</td>
			<td bgcolor="green">6</td>
    	</tr>
		<tr>
        	<td>第4次冒泡</td>
        	<td>2</td>
			<td>1</td>
			<td bgcolor="red">3</td>
			<td bgcolor="green">4</td>
			<td bgcolor="green">5</td>
			<td bgcolor="green">6</td>
    	</tr>
		<tr>
        	<td>第5次冒泡</td>
        	<td>1</td>
			<td bgcolor="red">2</td>
			<td bgcolor="green">3</td>
			<td bgcolor="green">4</td>
			<td bgcolor="green">5</td>
			<td bgcolor="green">6</td>
    	</tr>
		<tr>
        	<td>第6次冒泡</td>
        	<td bgcolor="red">1</td>
			<td bgcolor="green">2</td>
			<td bgcolor="green">3</td>
			<td bgcolor="green">4</td>
			<td bgcolor="green">5</td>
			<td bgcolor="green">6</td>
    	</tr>
	</table>
### 2.1.2冒泡排序API设计:  
<table>
		<tr>
			<th>类名</th>
        	<th>Bubble</th>
		</tr>
		<tr>
			<td>构造方法</td>
        	<td>Bubble()：创建Bubble对象</td>
		</tr>
		<tr>
			<td>成员方法</td>
        	<td>1.public static void sort(Comparable[] a)：对数组内的元素进行排序</br>2.private static boolean greater(Comparable v,Comparable w):判断v是否大于w</br>3.private static void exch(Comparable[] a,int i,int j)：交换a数组中，索引i和索引j处的值</td>
		</tr>
	</table>
### 2.1.3冒泡排序的代码实现    
> 

	public class Bubble {
	    /*
	     * 对数组a中的元素进行排序
	     * */
	    public static void sort(Comparable[] a) {
	        for (int i = a.length-1; i > 0; i--) {
	            for (int j = 0; j < i; j++) {
	                if (greater(a[j], a[j+1])) {
	                    exchange(a, j, j+1);
	                }
	            }
	        }
	    }
	
	    /*
	     * 比较v元素是否大于w元素
	     * */
	    private static boolean greater(Comparable v, Comparable w) {
	        return v.compareTo(w) > 0;
	    }
	
	    /*
	     *数组元素i和j交换
	     * */
	    private static void exchange(Comparable[] a, int i, int j) {
	        Comparable temp;
	        temp = a[i];
	        a[i] = a[j];
	        a[j] = temp;
	    }
	}

>

	import sort.Bubble;
	
	import java.util.Arrays;
	
	public class BubbleTest {
	    public static void main(String[] args) {
	        Integer[] arr = {4, 5, 6, 3, 2, 1};
	        Bubble.sort(arr);
	        System.out.println(Arrays.toString(arr));
	    }
	}
### 2.1.4冒泡排序的时间复杂度分析  
冒泡排序使用了双层for循环，其中内层循环的循环体是真正完成排序的代码，所以，我们分析冒泡排序的时间复杂度，主要分析一下内层循环体的执行次数即可。  
在最坏情况下，也就是假如要排序的元素为{6,5,4,3,2,1}逆序，那么：  
元素比较的次数为：  
(N-1)+(N-2)+(N-3)+...+2+1=((N-1)+1)*(N-1)/2=N^2/2-N/2;  
元素交换的次数为：  
(N-1)+(N-2)+(N-3)+...+2+1=((N-1)+1)*(N-1)/2=N^2/2-N/2;  
总执行次数为：  
(N^2/2-N/2)+(N^2/2-N/2)=N^2-N;  
按照大O推导法则，保留函数中的最高阶项那么最终冒泡排序的时间复杂度为O(N^2)  
### 2.1.5冒泡排序的算法稳定性  
冒泡排序就是把小的元素往前调或者把大的元素往后调。比较是相邻的两个元素比较，交换也发生在这两个元素之间。如果两个相等的元素相邻，那么它们之间没有发生交换；如果两个相等的元素没有相邻，那么即使通过前面的两两交换把两个相邻起来，这时候也不会交换，所以相同元素的前后顺序并没有改变，所以冒泡排序是一种稳定排序算法。  
