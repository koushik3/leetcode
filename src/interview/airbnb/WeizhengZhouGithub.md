rd list 和一个target word，要求输出在word list 里跟target 
word的edit distance 相差不大于k的所有words。我写了一个基于edit distance的解
法(见下面)，程序是要从头到尾都要写，包括main函数和test数据。写完后他问有没有
更好的解法，我说可以用trie，但是我不觉得我能在剩余时间里写得出来基于trie的解
法，就大致说了一下我认为的思路。在此也求大牛给一个基于trie解法的code。
link: http://www.mitbbs.com/article_t/JobHunting/32692817.html


Airbnb面试需要强调一下的是coding不用白板。电面是在一个类似于leetcode 的网站
上直接写code (有一些关键词高亮，但没有函数auto completion 和报错提示), 而
onsite则是给你一台有eclipse的电脑，要求编译通过并能通过面试官提供的测试例子
。我电面碰到的是一个白人小哥，刚毕业没多久，code题算法很简单但是比较考一些
edge case的处理。过程中聊得很开心。反馈回来说小哥直接给了strong signal, 免第
二轮电面onsite。Onsite总共有7轮：两轮culture fit, 两轮 coding, 两轮system 
design, 一轮 project deep dive。 过程就不再累述了。Coding 题非leetcode 原题
但属于中等难度。System design 主要是结合Airbnb网站自己的feature 来问。中间有
一个插曲：我第一个coding 的面试官来晚了15分钟，后来又花了大概10分钟setup 电
脑，题目出得也比较偏，以至于我最后没能完成code。好在我面试之后及时把情况反映
给了recruiter, 他调查属实以后，加上我其他几轮的表现不错，给我争取到了加面两
轮的机会。加面过程比较顺利，第一轮是白哥哥manager 问culture fit 和 behavior 
question, 顺利过。第二轮直接上来考coding, 超水平发挥，写了大概80~90行程序一
次编译运行通过。得到两个strong signal后拿到offer


1. regex match, slightly complicated version of http://leetcode.com/2011/09/regular-expression-matching.html
2. find maxium square inside a sqaure, similar to http://stackoverflow.com/questions/1726632/dynamic-programming-l
argest-square-block
3. edit distance


A家的题目跟Leetcode不是一个概念。
属于给你一个问题，你把model给出来，再写出代码，run，需要看到正确结果。
Coding interview考察点是：Can you illustrate the big picture of the problem?
Can you make something run?

Culture轮因人而异，有的人有3轮的。因为Airbnb是strong culture company，面试官
会从各个角度试探面试者的性格特征，包括旁敲侧击询问你跟朋友之间的愉快经历。最
好去看看A家CEO做的采访，对于“文化”的定义和意义。

给一个2d array，要求写一个顺序访问这个2d array的Iterator，包括hasNext()与
next()。注意2d array的每行中元素的个数可能不一样，也可能为空。followup是写一
个remove()，注意是remove当前item，不是下一个item。
要求code能运行。也没有bug free，bug fix得比较快，还是给onsite了。跪求版上面
过airbnb的大牛们的面经，包括culture fit的问题，可站内，多谢了！


题目：难度一般，很多字典和字符串的题目，多leetcode变体，代码量相对大
要求：在电脑上写，能把给出的不算刁钻的test case跑对
安排：电面一轮，onsite 6轮（3轮coding + 1轮project deep dive + 2轮culture 
fit）
特点：1. 面试官把标准答案记得很清楚，需要在写之前把思路细节讲清楚并优化到最
优，能少用一点空间就少用一点，即使不能在数量级上产生影响。2. culture fit很独
特但也没有十分刁难，喜欢了解他们商业模式，爱学新东西，有common sense的人

Airbnb的题目往往都很啰嗦，其实简单几句话就可以概括的。要求代码写完了能够编译，然后自己写测试用例并跑过。感觉这样的好处是的确很考察代码功力，那种当场一次bug free，然后跑几个测试用例全过的感觉很爽。不好的地方是容易增加变数，因为即使自己本身水平不变，不同时候发挥略有差异，检查一两个bug用的时间可能就没机会做后面的follow up了。
第一轮实现分页显示。给了以下一些输入数据，要求将以下行分页显示，每页12行，其中每行已经按score排好序，分页显示的时候如果有相同host id的行，则将后面同host id的行移到下一页。
[
"host_id,listing_id,score,city",
"1,28,300.1,SanFrancisco",
"4,5,209.1,SanFrancisco",
"20,7,208.1,SanFrancisco",
"23,8,207.1,SanFrancisco",
"16,10,206.1,Oakland",
"1,16,205.1,SanFrancisco",
"6,29,204.1,SanFrancisco",
"7,20,203.1,SanFrancisco",
"8,21,202.1,SanFrancisco",
"2,18,201.1,SanFrancisco",
"2,30,200.1,SanFrancisco",
"15,27,109.1,Oakland",
"10,13,108.1,Oakland",
"11,26,107.1,Oakland",
"12,9,106.1,Oakland",
"13,1,105.1,Oakland",
"22,17,104.1,Oakland",
"1,2,103.1,Oakland",
"28,24,102.1,Oakland",
"18,14,11.1,SanJose",
"6,25,10.1,Oakland",
"19,15,9.1,SanJose",
"3,19,8.1,SanJose",
"3,11,7.1,Oakland",
"27,12,6.1,Oakland",
"1,3,5.1,Oakland",
"25,4,4.1,SanJose",
"5,6,3.1,SanJose",
"29,22,2.1,SanJose",
"30,23,1.1,SanJose"
]
这题的思路不难，但是实现起来还是有点难度的。在遍历的时候需要维护一个LinkedHashMap作为page并且完成去重。用LinkedHashMap的好处是可以保证所有的entry是按插入的顺序排序的，所以仍然可以保证按score排序的性质。另外，一旦遇到相同的host_id，则将其对应的行存到另一个buffer里。由于需要变遍历边增减容器里的数据，需要用ListIterator，并调用remove和add方法。之前只用过remove，从来没用过add。
第二轮是他家一道高频题，给一堆租房的request，作为输入数组，找一个array subset，其中任意两个元素不能相邻，（因为要打扫房间），求使得子集里所有元素之和最大。一维DP解之，另外可以使用滚动数组让空间开销为常数。
第三轮是实现一个CSV格式的Parser。其中处理转义字符比较tricky，当时只给了三个最基本的test case，所以都过了，但是由于花了些时间debug，有些特殊情况一开始处理错了，后来没时间进行处理了。这一轮面得很郁闷，面试官没怎么理我，感觉在做自己的事情，没什么交流。测试的时候把不小心把输入内容给贴错了，花了不少时间检查。
他家的题目感觉除了第二轮实现起来简单，其它的题目都要写不少代码，45分钟码完bug free的确不简单。


Airbnb，
Phone Interview 09/23
给一个整数数组，求不相互挨着的数字可以想加得到的最大和
简单动归，半小时也差不多，不过不知道第二天直接受到拒信，发邮件求reconsider还被回复there is no feed back，楼主欲哭无泪，被dream company拒成这个样子也是醉了。。另外提一句，这一家的HR phone screen好像也比较重要，听说过几个同学跟HR聊了之后就没有下文的，所以各位同学还是注意一下。


题目：
给一个数组代表reservation request，suppose start date, end date back to back.
比如[5,1,1,5]代表如下预定：
Jul 1-Jul6
Jul6-Jul7
Jul7-Jul8
jul8-Jul13
当然最开始那个Jul 1是随便选就好的啦。
现在input的意义搞清楚了。还有一个限制，就是退房跟开始不能是同一天，比如如果接了Jul 1-Jul6，Jul6-Jul7就不能接了。那问题就是给你个数组，算算最多能把房子租出去多少天。这个例子的话就是10天。
[4,9,6]=10
[4,10,3,1,5]=15
思路是用DP，我解题的code：
private static int getMax(int[] requests){
int len=requests.length;
8 b0 C6 q8 t% Z5 y) S: B2 j* y
int first=0;
int second=0;
for(int i=0;i int temp=Math.max(requests+first,second);
first=second;
second=temp;
}
return second;
}
评论：move on到下一轮phone interview了。想必大家听说过Airbnb是在一个类似于LeetCode的网站写完直接运行test的，test还是在main函数里自己写，不是像LeetCode那样自动test。这个题我叙述的时候已经把很多没有用的废话去掉了，当时他讲给我的时候还有各种废话，把题意弄懂大概花了10min。然后刚开始我老想用greedy，浪费了一些时间。想到dp之后不知道怎么脑子打结又迷糊了半天，后来只剩15min才想清楚，6min写完code，4min写test并直接全对，剩五分钟瞎聊了一会儿。最惊险的一次电面。这思路回头再看是非常简单。


Airbnb: phone screen #1: 不相邻的range 求和最大 [check-in date, check-out date/ check-in date, check-out date/ check-in date,….]求最多能租出去几天。
phone screen #2: waived.
Airbnb: onsite #1. Project Deep Diving
onsite #2. Behavior Cultural Fitting
onsite #3. Code: WordBreak 不许用brute force.
onsite #4. Code: Text Justification
onsite #5. Ping server: output the timestamp offset
Dropbox: Given a pattern and a string input – find if string follows the same pattern and return 0 or 1. Examples: 1) Pattern : “abba”, input: “redblueredblue” should return 1. 2) Pattern: “aaaa”, input: “asdasdasdasd” should return 1. 3) Pattern: “aabb”, input: “xyzabcxzyabc” should return 0.
先给你有空格的版本：例如 pattern: “a a a a” input : “asd asd asd asd” 后给你没空格的版本：例如 Pattern: “aaaa”, input: “asdasdasdasd”


Airbnb，
Phone Interview 09/23
给一个整数数组，求不相互挨着的数字可以想加得到的最大和
简单动归，半小时也差不多，不过不知道第二天直接受到拒信，发邮件求reconsider还被回复there is no feed back，楼主欲哭无泪，被dream company拒成这个样子也是醉了。。另外提一句，这一家的HR phone screen好像也比较重要，听说过几个同学跟HR聊了之后就没有下文的，所以各位同学还是注意一下


Edit Distance


1. find all the combinations of a string in lowercase and uppercase. For example, string "ab" -> "ab", "Ab", "aB", "AB". So, you will have 2^n (n = number of chars in the string) output strings. The goal is for you to test each of these string and see if it match a hidden string.

2. Implement a simple regex parser which, given a string and a pattern, returns a booleanindicating whether the input matches the pattern. By simple, we mean that the regex can only contain special character: * (star), . (dot), + (plus). The star means what you'd expect, that there will be zero or more of previous character in that place in the pattern. The dot means any character for that position. The plus means one or more of previous character in that place in the pattern.


Store a set of sudden-death tournament results in a compact format (eg. a bit array) and a set of predicted match results (also in a bit array). Score the predictions, giving one point per correctly guessed match, without unpacking the bit array into a more convenient format (ie. you have to traverse the tree in-place).  


Find all words from a dictionary that are x edit distance away. 

Describe what happens when you enter a url in the web browser  

Sort a list of numbers in which each number is at a distance k from its actual position  


You have a plain with lots of rectangles on it, find out how many of them intersect  

two dimensional word permutation problem  


Given a dictionary, and a matrix of letters, find all the words in the matrix that are in the dictionary. (Going across, down or diagonally)  
