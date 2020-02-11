网络协议  
1. RPC vs HTTP  
2. UDP vs TCP  
3. TCP 三次握手 vs 四次挥手  
4. 滑动窗口的实现  
5. TCP的一些实现细节  
  
数据库  
1. 如何建立索引  
2. 事务  
其他的没回答也没记住


Android system passcode  
123  
456  
789  
>= 四点连线密码题，每个只能用一次，不能跨数字, 求4-9个点的所有密码数
被连到的数字可以跨比如2-1-3是合法的, 16可以直接连因为中间没数字  
就大概写了个思路 大概就是用DFS然后每新连一个数字就更新周边数字可以连接的数字

**一面技术面（约60分钟）：**  
1. 简单自我介绍  
2. 关于项目介绍，期间提到并发多线程，所以面试官引出一个问题  
  
3. 写一个变量i++的代码，要求保证线程同步。  
——类似于读写锁，楼主用Synchronized 给 object方法写了Lock() 和 UnLock()锁实现。  
追问：锁的机制是如何实现的：object锁还是方法锁？  
——回答的object锁，感觉面试官反馈不太对，也没有追问了。  
4. Http协议，详细介绍下浏览器输入[www.baidu.com](http://www.baidu.com/)之后的过程  
——DNS，GET, POST方法都涉及到了。  
追问TCP/IP 三次握手过程，为什么需要三次？  
—— 介绍TCP/IP过程，然后第三次保证信息同步，服务器需要知道客户端收到response的反馈  
追问如果第三次握手丢包怎么办？  
——服务器重新发送response一定次数，直到client回复，若超过次数则断开连接  
5. 为什么说TCP/IP是可靠传输？  
——拥塞控制，超时重传，滑动窗口  
6. 介绍下Java GC机制  
——计数器法，可达性算法  
追问可达性算法  
——GC root从跟节点树引用遍历，如果没有被引用的对象则被回收，  
追问如何判断引用？  
——举例创建一个object会添加一次引用  
追问jvm如何知道什么时候回收？  
——举例类似读写操作，可以调查read.gc()方法来触发；  
7. 数据库相关，SQL语句熟不熟？出了一个双表查询算平均分的题  
——楼主表示不太熟，马马虎虎写了一个select语句，面试官也没有追问了  
8. 数据库事务隔离机制  
—— 未提交读，提交读，可重复读，序列化, 分别介绍了可能存在的问题依次是脏读，不可重复度，幻读  
追问MySQL用的哪种？  
——可重复读  
追问如何实现的？  
——不太清楚，某种读写锁？  
追问MySQL索引怎么实现？  
——B+ Tree  
追问能否实现以下？  
—— (wtf？？？)实现下B+树？？？直接放弃，说可以解释下原理，面试官直接说不用解释了。。。  
9.算法题 ABC全排列，dfs+back tracking秒了，少许错误  
  
**二面技术面（约40分钟）：**  
1.自我介绍  
2. 楼主之前搞安全的， 追问你知道哪些安全攻击，介绍下xss？  
——表示某种注入攻击，具体不太熟，然后说 syn, dos, ddos可以  
追问介绍下dos  
——拒绝服务攻击，伪造报文向服务器发送大量请求，造成服务器过载，无法提供正常服务，ddos加分布式  
3.介绍 https  
——在http 基础上添加了ssl ，对称秘钥加密体制，公钥加密，私钥解密，然后又介绍了下非对称加密  
4. 介绍下进程死锁  
——4个条件：互斥，占有等待，非抢占，循环等待。分别解释了下  
5.解释下Java创建一个object，如何创建的，内存怎么分配的？  
——有点懵逼？ 举例创建一个String，系统会给这个Object分配一个内存地址，然后加引用指针，然后存入value值。  
追问equals 和 hashcode方法  
——equals判断value是否相等，hashcode通过hash function计算，这里答的不太好。。。  
6. 介绍信Java如何实现线程同步  
—— synchronize, lock, volatile, atomic  
追问解释下volatile  
——从Java 内存开始解释，然后解释了可见性，原子性，有序性  
追问乐观锁与悲观锁  
——乐观锁可以挂起做其他事情，悲观锁一直等待  
7.算法题 trap rain，留了20分钟，楼主15分钟不到bug free秒了，用two pointers.  
  
**三面BOSS面（约30分）:**  
1. 简单自我介绍  
2. 最近有看什么书啊？  
3. 为什么实习，之前的实习收获了什么，想从实习中学什么？  
4. 结束下浏览器是如何知道哪些客户的，与服务器怎么交互？  
——cookie 和session解释了一通  
5. 算法题 next permution 1234 -> 1243，先要求解释一下算法，大概用了8分钟，然后要求7分钟内写完代码？？？楼主只完成了一种case。。。  
6. linux熟悉哪些指令？  
7. 关于业务有什么想问的？  
  
总体下来感觉还是比较难的，楼主面试美西时间22：00，直到凌晨0：20左右结束，非常疲惫，体验一般。  
字节跳动（头条）还是比较注重计算机基础知识，非科班的可能有点吃力。前期多刷刷面经，多背背书就好。

第二题  
输入一个List<TaxiOrder>, 定义如下:  
class TaxiOrder {  
public int start_time;  
public int end_time;  
public int profit;  
}  
假如你只有一辆taxi, 能获得的最大利润是多少?  
后续: 假如你有n辆taxi来接单, 能获得的最大利润是多少?  
可以假定输入的List已经按照你的要求排好序了.

过滤掉一个vector<string>中返回频率最高的前k个string, 楼主上去一个手写堆然后分析了一波复杂度

1 Given a collection X of unsorted numbers, and factor Y,  
2 output all the numbers in [min, min*Y].  
3 min = Min(X)  
4 Y = 100% ~ 1000%  
5  
6 For example,  
7 Input X: [ 8, 10, 3, 15, 18, 2, 6, 16, 16]  
8 factor Y: 150%  
9  
10 Output: [4,5,6]  
11 Explanation: Min(X) = 2, so the range is [2, 2*150%=3]  
12  
  
可以扫两遍用O（2N）但是要求要更好，经提示，用了Priority Queue，maintain pq top是永远小于currentMin的。  

> function foo(nums, factor) {  
> if(!nums.length)  
> return [];  
>   
>   
> let currentMin = Number.MAX_SAFE_INTEGER;  
> let pq = new PriortyQueue(max);  
>   
> for(let i = 0; i < nums.length; ++i) {  
>   
> if(nums _* factor < currentMin ) {  
> pq = new PriortyQueue(max);  
> pq.push(nums[i);  
>   
> } else if(nums _<= currentMin) {  
> while(pq.top() > nums _* factor) {  
> pq.pop();  
> }  
> } else if(nums _<= currentMin * factor) {  
> pq.push(nums_);  
> }  
>   
> currentMin = Math.min(currentMin, nums_);  
> }  
>   
> let result = [];  
> while(pq.size())  
> result.push(pq.pop());  
>   
> return result;  
>   
> }______

  
  
**补充内容 (2019-12-5 21:38):**  
output 是 2，3 刚刚上面写错了

第一题，如何在一个单位球面上uniformly sample点。只要意识到gaussian是isotropic的就很显然了。  
  
第二题，连续扔骰子，扔出一个单调不减序列且最终抵达6算作成功（直接扔出6也算成功），问成功序列的期望长度是多少。出这个题的时候面试官也说这比较难，提示是可以把每个数字上停留的次数当成是一个geometric distribution。  
  
最后的coding题是算median of stream data，面试官说是leetcode原题，我题做得很少并没见过，不过仔细想想很简单，只要用heap来keep前半段max和后半段的min然后适当插入就好了。最后分析一下复杂度，也不是很难算。

原题是 蠡寇 懿廝鳞  
改动:  
输入：字典变成了哈希表，每个单词都有一个权重，表示这个单词在所有文章里面出现的概率。  
输出： 不要求找到所有分词的以后的句子，而是要求找到最优的分词之后的句子  
  
  
我自己的思路：  
还是正常找到所有可能的分词后的句子，思路和原题一样。  
之后对于每一个句子打一个分，然后输出分最高的句子。  
打分的方式： 把句子里面每个单词的概率相加。  
  
面试官比较纠结为什么不是把每个单词的概率相乘。我扯了相乘的浮点数太多以后会溢出 （每个单词的概率都是0.01， 0.05 之类的），丢失精度。还扯了机器学习里面期望函数如果是概率相乘都会取log,然后变成加法。  
面试官还问了这种方式会有什么问题， 我答了这种方式没有考虑到条件概率，比如， 如果 单词A 前面出现的单词是B 和C的话，对于单词A 的概率应该是不同的。 本来还想扯隐马尔可夫模型，结果很多细节都忘了。。话到嘴边就咽回去了。  
 
 最优确实概率最大  
  
相乘会有个问题  
比如，对于一个 sentence S=[W1,W3,..,Wn]  
score(s) = p(W1) * p(W2)*...*p(Wn)  
  
score(s) 最后会over flow, 如果 Word probabiloity 都很小，比如等于0.00000001 ， 而且n 很大 比如 n=100.  
  
  
相加和 相乘是一样的，相当于  
log(score(s)) = log( p(W1) * p(W2)*...*p(Wn)) = log( p(W1) ) + log( p(W2) ) + ... + log( p(Wn) )  
  
相加相当于我们最后求 log(score(s)) 的最优


有道理。那不应该直接求和。  
  
但是为了防止多个小的浮点数相乘溢出，对每个概率取log 相加比较make sense  
log(0.8) + log(0.0000001) = -7.1 < log(0.1) + log (0.1) = -2

**一面：**  
面试官人很nice，没有特别紧张的感觉；  
算法：从上到下从左到右打印二叉树（是我为数不多准备过的coding题）；  
根据简历自我介绍，简历项目，ML基础知识（MLE, MAP）  
  
**二面：**  
收到第二轮面试也很快！面试官是speech背景的manager；  
面试官对speech非常擅长，所以speech那个项目的问题在面试中占了很大部分；  
项目问的很细，features (mfcc)，training的各个环节。因为LZ对speech的知识掌握不扎实，简历上这部分答得并不是很好；  
还有，NLP的attention机制实现，ML(logistics)  
  
二面之后从邮件收到了reject，心情还是比较低落，因为准备不够充分，也觉得没有足够的经历去充实简历。  
  
总的来说，北美字节跳动AI Lab可能对你的speech的背景要求比较高，HR效率也很高。 LZ会再接再厉，经验供大家参考，祝同学们面试好运！

两轮都是coder视频面试，  
  
第一轮面试前两小时通知面试官有事面不了了，推了一周，第二周面试面试官人直接没了，打电话没人接，发邮件没人回。。。  
三四天后recruiter联系说抱歉，面试官有重要会议没结束。重新约时间，面试官回国出差，约在了美东半夜。  
主要聊research，一个一个过简历，面试官人很好，基本同一方向，聊得内容都懂，聊起来很轻松，最后问了到比较简单的coding，写了五分钟吧，就结束了  
  
第二天通知约了第二轮  
  
第二轮面试，面试官ML方向。楼主system方向，和ml基本没啥关系  
面试官全程不问简历，盯着ML基础知识开始问，什么推导SVM之类的。楼主本人只是几年前上过ml课，平时research和ml没啥关系，ml只是只停留在基本概念和简单的应用场景。 面试官全程基本都在问他的方向即ml,完全不想让我介绍自己的方向。coding 是median of data stream，讲了思路之后让coding，我个人用c++,面试官貌似只会Python，听说后就说那你别写了。后面有问了会不会红黑树，讲了个大概然后问我会不会写。。。最后又让实现一个sqrt of float, 大概是用梯度下降解，我不会。面试官全程笑嘻嘻，总说没事，不是你方向，掌握这么多可以了  
  
一周后挂了。

  
  
  
个人感受：挂了我认，确实第二轮好多问题回答不上来。  
但个人认为这种面试毫无意义，面试内容和岗位毫无关系，面试官对我的领域完全不懂，我不认为面试官有能力在这一轮担任面试官，或者说在跟我show off么？位置互换我也有能力让面试官一个问题回答不上来。。。candidate的时间也是时间，不该这么浪费别人时间  
以后应该不会面他们家了，虽然听说钱多。一方面个人水平不够支撑全领域精通，另一方面如此的混乱面试安排，并且完全没有提前告知会有其他方向的知识考查，也反映出该公司内部可能也有所混乱吧。  
  
好的方面： 第一轮面试官我觉得人很好，recruiter/hr 回邮件还算及时。
sqrt of float用gradient descent写，和我考的一样……我挂了已经

编程题  
given a circle with 10 nodes, 0->1->2....->9->0, start from 0 node, if allow to move n steps, what is the total number of different paths that the move ends at 0 (start point and end point are same).  
For example,  
  
n = 2, total number of different paths = 2: 0->1->0, 0->9->0  
n = 4, total number of different paths = 4: 0->1->2->1->0, 0->9->8->9->0, 0->1->0->9->0, 0->9->0->1->0

dp? dp[i, k]存的是走了k步走到i的路线数  
dp初始化全为0，起点在0，dp[0,0] = 1  
每次可以往左或者往右走一步，且是环  
所以dp[i, k] = dp[(i+1)%10, k-1] + dp[(i-1)%10, k-1]  
最后返回dp[0, n]  
然后每次更新第k列的时候，都只会用到k-1列，所以可以用rolling dp[i, k&1] 把空间降到O(20)  

[Python]  _纯文本查看_  _复制代码_

[?](https://www.1point3acres.com/bbs/#)

01

02

03

04

05

06

07

08

09

10

`def` `count_path(N):`

`dp` `=` `[[``0``,``0``]` `for` `_` `in` `range``(``10``)]`

`dp[``0``][``0``]` `=` `1`

`for` `k` `in` `range``(N):`

`for` `i` `in` `range``(``10``):`

`dp[i][k``+``1``&``1``]` `=` `dp[(i``-``1``)``%``10``][k&``1``]` `+` `dp[(i``+``1``)``%``10``][k&``1``]`

`return` `dp[``0``][N&``1``]`

`# count_path(2) = 2`

`# count_path(4) = 6`

补发一个字节跳动EA部门的面经。1面：leetcode原题 Add Two Numbers（做出来了）  
然后问了些基础面试问题：  
1.谈谈java String，StringBuilder，StringBuffer的区别;2. HashMap和ConcurrentHashMap的区别；3.mysql的索引数据结构是什么，简单说一下mysql的索引；4. 垃圾回收有哪些常见算法；  
5.jvm的类加载机制是什么，tomcat是怎么做类加载的，当两个项目都要导入到tomcat运行，是怎么加载的？（大概是这么问的？）6.TCP的为什么三次握手，四次挥手？挥手中第四次挥手用了多长时间？为什么用这么长时间；  
  
2面：题目：可google“字节跳动电容”，会有相关题目出现。  
  
3面：最大公共子序列问题 + leetcode原题 gas station，再问了一些其他关于项目的问题

**_题目_** 给一个数组和target，找出最长的subarray && sum==target，用接近O(N)的时时间  
  

-   问了数组是否有序和有无重复
-   刚开始可以用暴力破解
-   然后面试官提示说觉得哪些地方可以优化，个人觉得求和步骤太冗余了，所以想用前缀和，于是用preSum[idxRight] - preSum[idxLeft] = sum = target
-   这时最重要的一个环节来了, 就是研究这个公式就能有接近有O（n）解法, 最终解法preSum + Map<Integer, List<Integer>>

1. Given a tree (many children), find the node with the smallest average distance to all other nodes [bytedance]  
  
我面完之后自己又整理了一遍  

[Python]  _纯文本查看_  _复制代码_

[?](https://www.1point3acres.com/bbs/#)

01

02

03

04

05

06

07

08

09

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

54

55

56

57

58

59

60

61

62

63

64

65

66

67

68

`class` `Node:`

`def` `__init__(``self``, value):`

`self``.value` `=` `value`

`self``.children` `=` `[]`

`def` `add_children(``self``, children):`

`self``.children` `=` `children`

`def` `get_smallest_distance_sum(root: Node):`

`if` `root` `is` `None``:`

`return` `None`

`n` `=` `0`

`s` `=` `0`

`level` `=` `0`

`q` `=` `[root]`

`level_count` `=` `1`

`while` `len``(q) >` `0``:`

`next_level_count` `=` `0`

`while` `level_count >` `0``:`

`current` `=` `q.pop()`

`if` `current` `is` `not` `None``:`

`n` `+``=` `1`

`s` `+``=` `level`

`for` `child` `in` `current.children:`

`q.insert(``0``, child)`

`next_level_count` `+``=` `1`

`level_count` `-``=` `1`

`level` `+``=` `1`

`level_count` `=` `next_level_count`

`mapping` `=` `dict``()`

`get_sub_children_count(root, mapping)`

`result` `=` `{root: s}`

`update(root, n, mapping, s, result)`

`min_value` `=` `float``(``'inf'``)`

`min_node` `=` `None`

`for` `node, value` `in` `result.items():`

`if` `value < min_value:`

`min_node` `=` `node`

`min_value` `=` `value`

`return` `min_node`

`def` `update(root, n, mapping, s, result):`

`for` `child` `in` `root.children:`

`new_s` `=` `s` `-` `mapping[child]` `+` `(n` `-` `mapping[child]` `-` `2``)`

`result[child]` `=` `new_s`

`update(child, n, mapping, new_s, result)`

`def` `get_sub_children_count(root, result):`

`if` `root` `is` `None``:`

`return` `result`

`s` `=` `0`

`for` `child` `in` `root.children:`

`s` `+``=` `1` `+` `get_sub_children_count(child, result)`

`result[root]` `=` `s`

`return` `s`

`n1` `=` `Node(``1``)`

`n2` `=` `Node(``2``)`

`n3` `=` `Node(``3``)`

`n4` `=` `Node(``4``)`

`n5` `=` `Node(``5``)`

`n6` `=` `Node(``6``)`

`# n2.add_children([n4, n5])`

`# n3.add_children([n6])`

`# n1.add_children([n2, n3])`

`print``(get_smallest_distance_sum(n1).value)`

  
  
  
2. How to check a binary tree is complete binary? LC  
3. Given a list of integers, partition it into 2 subsets so the difference is minimized. (NP-hard问题大哥！）

给一个矩阵，矩阵的每个元素的值代表对应台子的高度。现在开始往矩阵里面注水，每过一小时水位涨1个单位。现在有一个游泳者，想从左上角游到右下角，问注多少时间的水他可以直接游过去而不用上台子？  
我用二分法+BFS做的，二分法查找最优的天数，BFS返回能不能到右下角。  
还要注意一下Corner case和常数时间的优化。

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExMjgxNywxMzE2MjI2ODYxLDI4OTI5MT
hdfQ==
-->