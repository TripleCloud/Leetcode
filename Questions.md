

利特扣得 二四二. Valid Anagram

给你一个人的日程表，要求你返回他所有有空的时间，  
比如: [8:30, 9:30], [9:00 : 12:30],[12:45, 12:50]  
返回就应该是 【0:00 - 8:30][12:30, 12:45][12:50, 24:00]  
注意这里要自己定义input的type

给你一个老版九宫格的手机键盘，给你一串数字，给你一个dictionary( list of strings)，让你返回valid word 在老版手机上（2 -> a, b, c ）(3 -> d, e, f) ....  
input可以使 2 2 2 3 46 2什么的

第一道题是从linkedlist里面消除所有值为n的node，输入为（Node head，int n），输出是Node，比如 2 -> 3 -> 3-> 4 -> 2, 需要删除2，则返回为3 -> 3 -> 4。这道题比较简单，做完了以后在白纸上跑了一个例子和edge case。第二道题是输入一系列的公司名称和股票值的信息，如果公司信息和股票价值的data是已有的，则需要在旧的value上加上新的股票值，例如（“MSFT”，400），（“FB”，200），（“MSFT”，300）输入后，MSFT会更新为700。需要完成两个操作，一个为得出当前股票值最高的公司，如果有很多公司都是最高值，则返回一个公司名称，第二个函数需要返回K个top公司。一开始想到了用HashMap和priority queue做，被问到priority queue按照什么排序，如果又添加data怎么办，意识到priorityqueue每次在做修改的时候需要重新添加排序，在这里我又提到了TreeMap，key为股票值，value为公司名字的set。我又分析了如果只用TreeMap，当有修改的时候不知道对应公司之前的股票值为多少，需要对TreeMap的所有key遍历一遍找到对应的公司，面试官提示可以用HashMap和TreeMap一起做，在这个提示下完成了代码。

[刷题](http://www.1point3acres.com/bbs/forum-84-1.html)网146， 171。 171 答得磕磕绊绊不过还是过了，第二天约下周onsite  
  
一轮：刷题网116，马拉松，biginterger 的ood （一小时）  
二轮：刷题网621，纽约地铁 ood（一小时）

1. 包装过的min stack  
2. 给一堆冰块，在每个时刻都会有从左从右从上方吹来的风融化暴露的冰块，问在哪个时刻冰块会全部融化
Math.min(maxHeight, (maxWidth + 1) / 2 )

3. 一个矩阵里面是海拔高度，从第一列中间的点开始倒水，判断会不会留到两边。  
很简单 DFS + memo, 注意判断visited  
4. LFU

1029. Two City Scheduling


嚟蔻 尔巴叁 和  
一个乱序的二叉树，保持原有的struct的情况下输出二叉搜索树

[系统设计](http://https//www.educative.io/courses/grokking-the-system-design-interview?affiliate_id=5749180081373184/)：  
搜索引擎中 紫东 布泉的功能  
问了很多follow up  
  
top k的股票问题 + follow up

设计一个ArrayList类，有许多followUp，其实更多的是和面试官讨论怎样implement更好一些  
设计一个可以随时取出栈中最小元素的stack  
第二轮：  
蠡口鹅伞🤙  
蠡口起就起

[刷题](http://www.1point3acres.com/bbs/forum-84-1.html)网叁四期变种  
刷题网妖酒酒变种  
  
二面  
聊简历，讲实习经历，实习中最有挑战的部分，why BB  
OOD，设计股票，有很多支股票input，要求写function返回某只股票的平均价格。有很多follow up，记不太清了  
follow up 1: 返回任意时间点，某只股票的平均价格(函数的Input这次多了个int时间)  
follow up 2: 返回最多股数的K支股票  
  
刷题网散酒气原题

1. 找数组中位数，quickselect  
  
2. dp计算矩阵最小乘法次数
1. NYC 地铁题  
2. 黎蔻 伞久四  
2轮：  
1. datastream top K 三个小问  
（1）不同公司 只保留most recent 10 个 datastream （用了map + queue）  
（2） multi-thread 情况：同时得到多个data: (checkpoint + xlock + commit）  
（3）对于不同公司， 累加对应quantity, 然后return top k quantity 的公司

  
  
（e.g. IBM: 1000, MS: 500, APPLE: 3000, IBM: 400）return (top 2): (Apple: 3000, IBM: 1400

第一轮两道题：lc 153 第二题 给一堆flight的信息 然后给一个start end 找所有能从start飞到end的route  
第二轮两道题：纽约地铁站面经 然后建一个sparse matrix的class

第一轮：  
1，一维candy crush，一个字符串如AABBBACD，出现3次及以上的字符消除，消除之后的如果也有这样的pattern继续消除，对于这个input A,B都会被消除，输出CD。做法是先压缩成(A,2),(B,3),(A,1),(C,1),(D,1)之后再扫描  
2，meeting rooms2  
  
第二轮：  
1，boundary of a binary tree LC原题  
2，N个人排成一个圈编号0~n-1，每次按顺时针方向给人一把刀，他会捅死自己顺时针方向的下一个人，返回最后活下来的人的序号

两个Byte类型的数组，分别为A和B。现给出target sum，问是否能从A和B中各找出一个数使得它们的和为target。  
比如：  
A=[1,5,3,6]  
B=[5,2,8,4]  
target=11  
返回true，因为存在3（in A) + 8 (in B) = 11  
楼主第一反应就是hashmap，简单直接。要求复杂度分析：Time -> O(n) Space -> O(n)  
然后面试官要求优化空间复杂度，楼主第二反应就是将A和B排序，然后two pointer找是否存在。Time -> O(nlogn) Space -> O(1)  
然后面试官要求继续优化，楼主思索片刻，发现是Byte数组，那么只要建立一个长为2^8的array来记录A中哪些数字存在，然后遍历B即可。Time -> O(n) Space -> O(1)  
最后要求实现一下，这里楼主写了一个bug：target - num有可能小于0而出现数组越界问题
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExOTk1MzQyNV19
-->