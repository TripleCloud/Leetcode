

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
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTEyNzU2ODddfQ==
-->