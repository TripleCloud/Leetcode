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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU1NjYwNDU4NywxMzE2MjI2ODYxLDI4OT
I5MThdfQ==
-->