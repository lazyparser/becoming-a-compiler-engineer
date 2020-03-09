# 编译技术入门与实战

## Cooper 教授 L17-IR 评注

### 0

从业多年之后才能看懂里面的感悟

### 1

Mea culpa is a Latin phrase that means "through my fault" and is an acknowledgement of having done wrong. Grammatically, meā culpā is in the ablative case, with an instrumental meaning. Wikipedia

amnesty 大赦天下

### 2

这里都是一些经验之谈。
刚开始肯定无法体会，没关系的。

cusp
/kəsp/
Learn to pronounce
noun
noun: cusp; plural noun: cusps

    1.
    a point of transition between two different states.
    "those on the cusp of adulthood"
    2.
    a pointed end where two curves meet.

Oxford Dict

这种乐趣门外汉是感受不到的，正所谓「初闻不识曲中意，再闻已是曲中人」。


### 3

说了编译器领域的共识。

前端 --IR--> 优化器

信息的表达方式决定了相关算法的能力

### 4

IR： 信息的载体。哪些信息上船，哪些放在显眼位置。

优化器能看到的只有IR，IR没有的都看不到。

现在IR中允许加入各种annotation/attributes，在不改变IR的情况下加信息。就像是货运船上的集装箱。

当你开始自己设计编译器的时候，或许你就可以理解 ambition 在这里的包含的感情了。

### 5 - 7

思维里的分析框架。

这些设计的考虑，我们这门课的朋友大概有一个概念认识就行。

设计的取舍需要时间，动手尝试很多组合之后，形成 **自己的经验和喜好** 。

### 8

index slide

下半部分在SDT中会讨论（存储模型在更后面）

### 9

IR形式上的分类
参考 EaC 书中的解释
基本上：树AST，链3AC，混合SSA

### 10

直观的例子，略。
一些前端的工作就是将左边的形式翻译成右边的形式（BytecodeBuilder 或 Generator）

### 11

抽象层次和数据组织形式不是统一的。
例如解释器执行使用的字节码就比较抽象。

### 12

静态代码检查和程序理解一般会用到语法树

### 13

你遇到语法解析树的可能性比较小。
静态代码检查和程序理解一般用AST，更简洁。
解释器有时候也可以直接用AST计算。

### 14

暂时不用深究，不懂没关系，后面用到。

注意这里 value 的涵义。value 是多义词。

value numbering 是一个很经典的算法。GVN基本都有实现。

### 15

这页内容是纯复习树的实现。
具体实现，比较简单。
二叉树和任意树转换算法看《数据结构》

### 16

稍微早了一点。这里是为了完整性。

依赖关系有数据的和控制流的，这里说的是BB内，不考虑控制流。
数据的关系是通过变量之间的 def use 体现的。后面有算法寻找到 def use 关系。（这里有兴趣推荐先看看燧原科技在B站公开的基于DCC888的公开课程，里面有详细介绍。本课程后续也会详细介绍这些算法。）

### 17

调用图要更后一点才遇到。
体现函数/方法之间的相互关系

提问：
dep graph 节点是？，边是？
CFG 的节点是？，边是？
callgraph 的节点是，边是？

### 18

di·gres·sion
/ˌdīˈɡreSH(ə)n/

noun: digression; plural noun: digressions

    a temporary departure from the main subject in speech or writing.

rant
/rant/

verb:
    speak or shout at length in a wild, impassioned way.
    "she was still ranting on about the unfairness of it all"

noun:
    a spell of ranting; a tirade.
    "his rants against organized religion"

技术细节，所有的对比都应该是整数比较，为了速度。
几乎所有的VM都会对字符串进行特殊的处理。
有的会对小字符串进行特殊处理，例如40字节以内的变量名或字面量。

后面就跟L18-IR的内容类似了。

### 19

index page

### 20

三地址的地址可以理解为operand
是概念上的3地址
最多不超过3个，可以少于3个

### 21

Quadruples 四元组 = 三地址 + opcode
所以可以有一张表格来表达
注意，数据流向是从左到右还是从右到左是喜好，没有唯一的规则。

### 22

Triples 三元组 = 三地址 + opcode - 结果operand
隐藏的去哪里了？去到行号（序列ID）里面了。

squint
/skwint/
look at someone or something with one or both eyes partly closed in an attempt to see more clearly or as a reaction to strong light.

### 23

不确定我的理解是否正确。
reorder 的是第一列，第二列不变。

### 24 - 25

考古：技术积累的重要过程。
计算机科学的历史很短，鼓励多阅读原始文献

### 26

二地址码可能就只有虚拟机里面了。
X86？
PDP-11 上古机型，有很多传奇可以考古

直接搜索 destructive operations 是医学解释，

### 27

栈指令集，操作数的制定可以嵌入到opcode里面。
例如 multiply a b -> c 可以假设 a b 在栈上，计算后 c 压栈。
最出名的是 JavaVM。
V8 解释器和 Dalvik 使用的 reg based。

如果你感兴趣，可以找：
Virtual Machine Showdown: Stack Versus Registers

### 28

index slide
