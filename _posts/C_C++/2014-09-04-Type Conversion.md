---
layout: post
title: Type Conversion
category: 游戏技术
tags: Ｃ／Ｃ＋＋
keywords: 
description: 
---

C++的类型转换符

使用标准C++的类型转换符：static\_cast、dynamic\_cast、reinterpret\_cast、和const\_cast。

1**<span style="color:#e53333;">static\_cast</span>**

用法：static\_cast\<type-id\>(expression) 

该运算符把expression 转换为type-id 类型，但没有运行时类型检查来保证转换的安全性。

它主要有如下几种用法：

①用于类层次结构中基类和子类之间指针或引用的转换。

  进行上行转换（把子类的指针或引用转换成基类表示）是安全的；

  进行下行转换（把基类指针或引用转换成子类表示）时，由于没有动态类型检查，所以是不安全的。

②用于基本数据类型之间的转换，如把int 转换成char，把int 转换成enum。这种转换的安全性也要开发人员来保证。

③把空指针转换成目标类型的空指针。

④把任何类型的表达式转换成void 类型。

注意：static\_cast 不能转换掉expression 的const、volitale、或者\_\_unaligned 属性。



2**<span style="color:#e53333;">dynamic\_cast</span>**

用法：dynamic\_cast\<type-id\>(expression)

该运算符把expression 转换成type-id 类型的对象。Type-id 必须是类的指针、类的引用

或者void\*；

如果type-id 是类指针类型，那么expression 也必须是一个指针，如果type-id 是一个引

用，那么expression 也必须是一个引用。

dynamic\_cast 主要用于类层次间的上行转换和下行转换，还可以用于类之间的交叉转换。

在类层次间进行上行转换时，dynamic\_cast 和static\_cast 的效果是一样的；

在进行下行转换时，dynamic\_cast 具有类型检查的功能，比static\_cast 更安全。

classB{

public:

 intm\_iNum;

 virtualvoidfoo();

};

classD:publicB{

 public:

 char\*m\_szName[100];

};

voidfunc(B\*pb){

 D\*pd1=static\_cast\<D\*\>(pb);

 D\*pd2=dynamic\_cast\<D\*\>(pb);

}

在上面的代码段中，如果pb 指向一个D 类型的对象，pd1 和pd2 是一样的，并且对这两

个指针执行D 类型的任何操作都是安全的；

但是，如果pb 指向的是一个B 类型的对象，那么pd1 将是一个指向该对象的指针，对它

进行D 类型的操作将是不安全的（如访问m\_szName），

而pd2 将是一个空指针。

另外要注意：B 要有虚函数，否则会编译出错；static\_cast 则没有这个限制。

这是由于运行时类型检查需要运行时类型信息，而这个信息存储在类的虚函数表（

关于虚函数表的概念，详细可见\<Insidec++objectmodel\>）中，只有定义了虚函数的

类才有虚函数表，没有定义虚函数的类是没有虚函数表的。

另外，dynamic\_cast 还支持交叉转换（crosscast）。如下代码所示。

classA{

public:

 intm\_iNum;

 virtualvoidf(){}

};

classB:publicA{

};

classD:publicA{

};

voidfoo(){

 B\*pb=newB;

 pb-\>m\_iNum=100;

 D\*pd1=static\_cast\<D\*\>(pb); //compileerror

 D\*pd2=dynamic\_cast\<D\*\>(pb);//pd2isNULL

 deletepb;

}

在函数foo 中，使用static\_cast 进行转换是不被允许的，将在编译时出错；而使用

dynamic\_cast 的转换则是允许的，结果是空指针。



3**<span style="color:#e53333;">reinterpret\_cast</span>**

用法：reinterpret\_cast\<type-id\>(expression)

type-id 必须是一个指针、引用、算术类型、函数指针或者成员指针。

它可以把一个指针转换成一个整数，也可以把一个整数转换成一个指针（先把一个指针转换成一个整数，在把该整数转换成原类型的指针，还可以得到原先的指针值）。

该运算符的用法比较多.

(static\_cast.与.reinterpret\_cast 比较，见下面)



4**<span style="color:#e53333;">const\_cast</span>**

用法：const\_cast\<type\_id\>(expression)

该运算符用来修改类型的const 或volatile 属性。除了const 或volatile 修饰之外， type\_id

和expression 的类型是一样的。

常量指针被转化成非常量指针，并且仍然指向原来的对象；

常量引用被转换成非常量引用，并且仍然指向原来的对象；常量对象被转换成非常量对象。

Voiatile 和const 类试。举如下一例：

classB{

public:

 intm\_iNum;

}

voidfoo(){

constBb1;

b1.m\_iNum=100; //comileerror

Bb2=const\_cast\<B\>(b1);

b2.m\_iNum=200; //fine

}

上面的代码编译时会报错，因为b1 是一个常量对象，不能对它进行改变；

使用const\_cast 把它转换成一个常量对象，就可以对它的数据成员任意改变。注意：b1 和

b2 是两个不同的对象。

=============================================

6

==dynamic\_cast.vs.static\_cast 

=============================================



classB{...}; 

classD:publicB{...}; 



voidf(B\*pb) 

{ 

D\*pd1=dynamic\_cast\<D\*\>(pb); 

D\*pd2=static\_cast\<D\*\>(pb); 

} 

IfpbreallypointstoanobjectoftypeD,thenpd1andpd2willgetthesamevalue.

Theywillalsogetthesamevalueifpb==0. 

IfpbpointstoanobjectoftypeBandnottothecompleteDclass,then

dynamic\_castwillknowenoughtoreturnzero.However,static\_castreliesonthe

programmer’sassertionthatpbpointstoanobjectoftypeDandsimplyreturnsa

pointertothatsupposedDobject. 

即dynamic\_cast 可用于继承体系中的向下转型，即将基类指针转换为派生类指针，比

static\_cast 更严格更安全。dynamic\_cast 在执行效率上比static\_cast 要差一些，但

7

static\_cast 在更宽上范围内可以完成映射，这种不加限制的映射伴随着不安全性。

static\_cast 覆盖的变换类型除类层次的静态导航以外，还包括无映射变换、窄化变换(这种

变换会导致对象切片,丢失信息)、用VOID\*的强制变换、隐式类型变换等... 





=============================================

==**static\_cast.vs.reinterpret\_cast **

=============================================

reinterpret\_cast 是为了映射到一个完全不同类型的意思，这个关键词在我们需要把类型

映射回原有类型时用到它。我们映射到的类型仅仅是为了故弄玄虚和其他目的，这是所有映

射中最危险的。(这句话是C++编程思想中的原话) 

static\_cast 和 reinterpret\_cast 操作符修改了操作数类型。它们不是互逆的；

static\_cast 在编译时使用类型信息执行转换，在转换执行必要的检测(诸如指针越界计算,

类型检查). 其操作数相对是安全的。另一方面；reinterpret\_cast 仅仅是重新解释了给出

的对象的比特模型而没有进行二进制转换， 例子如下：

intn=9;doubled=static\_cast \<double\>(n); 

上面的例子中, 我们将一个变量从 int 转换到 double。 这些类型的二进制表达式是不同

的。 要将整数 9 转换到 双精度整数 9，static\_cast 需要正确地为双精度整数 d 补足比

特位。其结果为 9.0。而reinterpret\_cast 的行为却不同: 

8

intn=9; 

doubled=reinterpret\_cast\<double&\>(n);

这次, 结果有所不同. 在进行计算以后,d 包含无用值. 这是因为 reinterpret\_cast 仅仅

是复制 n 的比特位到 d, 没有进行必要的分析. 

因此, 你需要谨慎使用 reinterpret\_cast.







