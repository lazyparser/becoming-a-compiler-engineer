# 编译技术入门与实战

## Cooper 教授 L19SDT-1 评注

SDT 可以理解为 parser 给了一个搭车构建AST、符号表的机会。
如何使用好 parser 给的 hooks，是靠经验技巧的。

### 0 - 5

略

### 6 Example: Type System

大名鼎鼎的「类型系统」。
类型系统是什么？带有强制检查保证的契约。

```C
int a; char b;
b = a; // BAD; Should fail?
string s; complex c;
s = s + c; // Depends.
```

### 7

例子：名字重载

```C
int i; // global
int foo() {
  int i; // function level
  {
    int i; // block
  }
}

```

```C++
class A { public: int i; };
class B: public A { public: int i;};

class A a;
class B b;

int main(){
	a.i = 3;
	b.i = 5;
	cout<<"a.i = "<<a.i<<endl;
	cout<<"b.i = "<<b.i<<endl;
	class A* p = &b;
	cout<<"p->i = "<<p->i<<endl;
}
```

### 8

例子：存储布局
这是操作系统或者修养里面会提到的知识。

### 9

图形化的展示下《连接器和加载器》
或者《程序员的基本修养》

### 10

迷惑：为什么要在这里提这个？

CU = compilation unit

### 11

linkers & loaders

### 12

ad-hoc

### 13

简单版本，其实用RE就足够表示。

### 14

现在是判别程序，只输出 true / false。

### 15 - 19

接下来SDT要获得具体的整数的数值。

吃进来的假设 256，先吃 2 ，再吃 5，再吃 6.
自然的，需要一个变量/寄存器/累加器来保存
2， 2*10+5， 25*10 + 6


### 20 - 25

对于 ACTION-GOTO 表忘记了的可以看 Parsing 部分的 slides， L14 到 L16

9 7 6 的吃法是
9， DL(9)， DL(97) 7， DL(97)， DL(97) 6， DL(976)， Number


### 26

$$ 默认类型是int，也可以自己设定类型。

### 27

小结。
属性文法在EaC中有写。差别可能第一遍看不出来有多大。

### 28 - 32

AHSDT = ad-hoc SDT
这里的代码骨骼是之前在Parsing部分的slides（以及书里）的内容。
